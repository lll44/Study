```
Source:
Tags: 
Last-Updated:
```

# Chapter 21Project: Skill-Sharing Website

> [](https://eloquentjavascript.net/21_skillsharing.html#p_ektEqTmX2a)If you have knowledge, let others light their candles at it.
> 
> Margaret Fuller

![Picture of two unicycles](https://eloquentjavascript.net/img/chapter_picture_21.jpg)

[](https://eloquentjavascript.net/21_skillsharing.html#p_lJLUX5aYTh)A _skill-sharing_ meeting is an event where people with a shared interest come together and give small, informal presentations about things they know. At a gardening skill-sharing meeting, someone might explain how to cultivate celery. Or in a programming skill-sharing group, you could drop by and tell people about Node.js.

[](https://eloquentjavascript.net/21_skillsharing.html#p_/pOZhwpvd/)Such meetups—also often called _users’ groups_ when they are about computers—are a great way to broaden your horizon, learn about new developments, or simply meet people with similar interests. Many larger cities have JavaScript meetups. They are typically free to attend, and I’ve found the ones I’ve visited to be friendly and welcoming.

[](https://eloquentjavascript.net/21_skillsharing.html#p_w7vSRf518o)In this final project chapter, our goal is to set up a website for managing talks given at a skill-sharing meeting. Imagine a small group of people meeting up regularly in the office of one of the members to talk about unicycling. The previous organizer of the meetings moved to another town, and nobody stepped forward to take over this task. We want a system that will let the participants propose and discuss talks among themselves, without a central organizer.

[](https://eloquentjavascript.net/21_skillsharing.html#p_We9gc8FghX)Just like in the [previous chapter](https://eloquentjavascript.net/20_node.html), some of the code in this chapter is written for Node.js, and running it directly in the HTML page that you are looking at is unlikely to work. The full code for the project can be downloaded from [_https://eloquentjavascript.net/code/skillsharing.zip_](https://eloquentjavascript.net/code/skillsharing.zip).

## [](https://eloquentjavascript.net/21_skillsharing.html#h_WbA1NnIRqT)Design

[](https://eloquentjavascript.net/21_skillsharing.html#p_MplsNwNLhr)There is a _server_ part to this project, written for Node.js, and a _client_ part, written for the browser. The server stores the system’s data and provides it to the client. It also serves the files that implement the client-side system.

[](https://eloquentjavascript.net/21_skillsharing.html#p_+06E4FMG7h)The server keeps the list of talks proposed for the next meeting, and the client shows this list. Each talk has a presenter name, a title, a summary, and an array of comments associated with it. The client allows users to propose new talks (adding them to the list), delete talks, and comment on existing talks. Whenever the user makes such a change, the client makes an HTTP request to tell the server about it.

![Screenshot of the skill-sharing website](https://eloquentjavascript.net/img/skillsharing.png)

[](https://eloquentjavascript.net/21_skillsharing.html#p_R3HdsDdi40)The application will be set up to show a _live_ view of the current proposed talks and their comments. Whenever someone, somewhere, submits a new talk or adds a comment, all people who have the page open in their browsers should immediately see the change. This poses a bit of a challenge—there is no way for a web server to open a connection to a client, nor is there a good way to know which clients are currently looking at a given website.

[](https://eloquentjavascript.net/21_skillsharing.html#p_sXOeE6mAl8)A common solution to this problem is called _long polling_, which happens to be one of the motivations for Node’s design.

## [](https://eloquentjavascript.net/21_skillsharing.html#h_Yxu7U155Cs)Long polling

[](https://eloquentjavascript.net/21_skillsharing.html#p_UARchLL3as)To be able to immediately notify a client that something changed, we need a connection to that client. Since web browsers do not traditionally accept connections and clients are often behind routers that would block such connections anyway, having the server initiate this connection is not practical.

[](https://eloquentjavascript.net/21_skillsharing.html#p_50FXIxQNGa)We can arrange for the client to open the connection and keep it around so that the server can use it to send information when it needs to do so.

[](https://eloquentjavascript.net/21_skillsharing.html#p_HuaXdPMyk3)But an HTTP request allows only a simple flow of information: the client sends a request, the server comes back with a single response, and that is it. There is a technology called _WebSockets_, supported by modern browsers, that makes it possible to open connections for arbitrary data exchange. But using them properly is somewhat tricky.

[](https://eloquentjavascript.net/21_skillsharing.html#p_Ho0D78j+/J)In this chapter, we use a simpler technique—long polling—where clients continuously ask the server for new information using regular HTTP requests, and the server stalls its answer when it has nothing new to report.

[](https://eloquentjavascript.net/21_skillsharing.html#p_jgdXNb8hyw)As long as the client makes sure it constantly has a polling request open, it will receive information from the server quickly after it becomes available. For example, if Fatma has our skill-sharing application open in her browser, that browser will have made a request for updates and will be waiting for a response to that request. When Iman submits a talk on Extreme Downhill Unicycling, the server will notice that Fatma is waiting for updates and send a response containing the new talk to her pending request. Fatma’s browser will receive the data and update the screen to show the talk.

[](https://eloquentjavascript.net/21_skillsharing.html#p_SAbyKs9a4Y)To prevent connections from timing out (being aborted because of a lack of activity), long polling techniques usually set a maximum time for each request, after which the server will respond anyway, even though it has nothing to report, after which the client will start a new request. Periodically restarting the request also makes the technique more robust, allowing clients to recover from temporary connection failures or server problems.

[](https://eloquentjavascript.net/21_skillsharing.html#p_G3JjyqG0SD)A busy server that is using long polling may have thousands of waiting requests, and thus TCP connections, open. Node, which makes it easy to manage many connections without creating a separate thread of control for each one, is a good fit for such a system.

## [](https://eloquentjavascript.net/21_skillsharing.html#h_a1H+QQ9w0g)HTTP interface

[](https://eloquentjavascript.net/21_skillsharing.html#p_Bc7qJWONLJ)Before we start designing either the server or the client, let’s think about the point where they touch: the HTTP interface over which they communicate.

[](https://eloquentjavascript.net/21_skillsharing.html#p_DAqJk8WjH9)We will use JSON as the format of our request and response body. Like in the file server from [Chapter 20](https://eloquentjavascript.net/20_node.html#file_server), we’ll try to make good use of HTTP methods and headers. The interface is centered around the `/talks` path. Paths that do not start with `/talks` will be used for serving static files—the HTML and JavaScript code for the client-side system.

[](https://eloquentjavascript.net/21_skillsharing.html#p_UHEQ70Qz7s)A `GET` request to `/talks` returns a JSON document like this:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_LnKGb3Adty)[{"title": "Unituning", "presenter": "Jamal", "summary": "Modifying your cycle for extra style", "comments": []}]

[](https://eloquentjavascript.net/21_skillsharing.html#p_aWz1ZbQjuM)Creating a new talk is done by making a `PUT` request to a URL like `/talks/Unituning`, where the part after the second slash is the title of the talk. The `PUT` request’s body should contain a JSON object that has `presenter` and `summary` properties.

[](https://eloquentjavascript.net/21_skillsharing.html#p_KfmhZR585o)Since talk titles may contain spaces and other characters that may not appear normally in a URL, title strings must be encoded with the `encodeURIComponent` function when building up such a URL.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_vixRLAECCO)console.log("/talks/" + encodeURIComponent("How to Idle")); // → /talks/How%20to%20Idle

[](https://eloquentjavascript.net/21_skillsharing.html#p_9WLYY3I2DU)A request to create a talk about idling might look something like this:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_G609VIyy0C)PUT /talks/How%20to%20Idle HTTP/1.1 Content-Type: application/json Content-Length: 92 {"presenter": "Maureen", "summary": "Standing still on a unicycle"}

[](https://eloquentjavascript.net/21_skillsharing.html#p_MlEec58Mz7)Such URLs also support `GET` requests to retrieve the JSON representation of a talk and `DELETE` requests to delete a talk.

[](https://eloquentjavascript.net/21_skillsharing.html#p_DdsHVoQpp3)Adding a comment to a talk is done with a `POST` request to a URL like `/talks/Unituning/comments`, with a JSON body that has `author` and `message` properties.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_JUbwWgr3xI)POST /talks/Unituning/comments HTTP/1.1 Content-Type: application/json Content-Length: 72 {"author": "Iman", "message": "Will you talk about raising a cycle?"}

[](https://eloquentjavascript.net/21_skillsharing.html#p_i78LNKoc4F)To support long polling, `GET` requests to `/talks` may include extra headers that inform the server to delay the response if no new information is available. We’ll use a pair of headers normally intended to manage caching: `ETag` and `If-None-Match`.

[](https://eloquentjavascript.net/21_skillsharing.html#p_aQzwhPBm+b)Servers may include an `ETag` (“entity tag”) header in a response. Its value is a string that identifies the current version of the resource. Clients, when they later request that resource again, may make a _conditional request_ by including an `If-None-Match` header whose value holds that same string. If the resource hasn’t changed, the server will respond with status code 304, which means “not modified”, telling the client that its cached version is still current. When the tag does not match, the server responds as normal.

[](https://eloquentjavascript.net/21_skillsharing.html#p_1IdVaazzeZ)We need something like this, where the client can tell the server which version of the list of talks it has, and the server responds only when that list has changed. But instead of immediately returning a 304 response, the server should stall the response and return only when something new is available or a given amount of time has elapsed. To distinguish long polling requests from normal conditional requests, we give them another header, `Prefer: wait=90`, which tells the server that the client is willing to wait up to 90 seconds for the response.

[](https://eloquentjavascript.net/21_skillsharing.html#p_JPz1jBPEDl)The server will keep a version number that it updates every time the talks change and will use that as the `ETag` value. Clients can make requests like this to be notified when the talks change:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_RikeEeOO6T)GET /talks HTTP/1.1 If-None-Match: "4" Prefer: wait=90 (time passes) HTTP/1.1 200 OK Content-Type: application/json ETag: "5" Content-Length: 295 [....]

[](https://eloquentjavascript.net/21_skillsharing.html#p_7W+awFFiIf)The protocol described here does not do any access control. Everybody can comment, modify talks, and even delete them. (Since the Internet is full of hooligans, putting such a system online without further protection probably wouldn’t end well.)

## [](https://eloquentjavascript.net/21_skillsharing.html#h_wTUn7xllPe)The server

[](https://eloquentjavascript.net/21_skillsharing.html#p_AXW7RPZDuT)Let’s start by building the server-side part of the program. The code in this section runs on Node.js.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_fRXdG+wuBV)Routing

[](https://eloquentjavascript.net/21_skillsharing.html#p_YGBPHzmANZ)Our server will use `createServer` to start an HTTP server. In the function that handles a new request, we must distinguish between the various kinds of requests (as determined by the method and the path) that we support. This can be done with a long chain of `if` statements, but there is a nicer way.

[](https://eloquentjavascript.net/21_skillsharing.html#p_sPoekSefGQ)A _router_ is a component that helps dispatch a request to the function that can handle it. You can tell the router, for example, that `PUT` requests with a path that matches the regular expression `/^\/talks\/([^\/]+)$/` (`/talks/` followed by a talk title) can be handled by a given function. In addition, it can help extract the meaningful parts of the path (in this case the talk title), wrapped in parentheses in the regular expression, and pass them to the handler function.

[](https://eloquentjavascript.net/21_skillsharing.html#p_l/CAybKBxr)There are a number of good router packages on NPM, but here we’ll write one ourselves to illustrate the principle.

[](https://eloquentjavascript.net/21_skillsharing.html#p_Neob32Zrxc)This is `router.js`, which we will later `require` from our server module:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_0cNWrBAXST)const {parse} = require("url"); module.exports = class Router { constructor() { this.routes = []; } add(method, url, handler) { this.routes.push({method, url, handler}); } resolve(context, request) { let path = parse(request.url).pathname; for (let {method, url, handler} of this.routes) { let match = url.exec(path); if (!match || request.method != method) continue; let urlParts = match.slice(1).map(decodeURIComponent); return handler(context, ...urlParts, request); } return null; } };

[](https://eloquentjavascript.net/21_skillsharing.html#p_bF2vPHSoGm)The module exports the `Router` class. A router object allows new handlers to be registered with the `add` method and can resolve requests with its `resolve` method.

[](https://eloquentjavascript.net/21_skillsharing.html#p_zGaZWr/Iyt)The latter will return a response when a handler was found, and `null` otherwise. It tries the routes one at a time (in the order in which they were defined) until a matching one is found.

[](https://eloquentjavascript.net/21_skillsharing.html#p_RvFMtSS5T/)The handler functions are called with the `context` value (which will be the server instance in our case), match strings for any groups they defined in their regular expression, and the request object. The strings have to be URL-decoded since the raw URL may contain `%20`-style codes.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_WmSQ4nnG8k)Serving files

[](https://eloquentjavascript.net/21_skillsharing.html#p_UEoXOYzg8q)When a request matches none of the request types defined in our router, the server must interpret it as a request for a file in the `public` directory. It would be possible to use the file server defined in [Chapter 20](https://eloquentjavascript.net/20_node.html#file_server) to serve such files, but we neither need nor want to support `PUT` and `DELETE` requests on files, and we would like to have advanced features such as support for caching. So let’s use a solid, well-tested static file server from NPM instead.

[](https://eloquentjavascript.net/21_skillsharing.html#p_09AEt7I4mE)I opted for `ecstatic`. This isn’t the only such server on NPM, but it works well and fits our purposes. The `ecstatic` package exports a function that can be called with a configuration object to produce a request handler function. We use the `root` option to tell the server where it should look for files. The handler function accepts `request` and `response` parameters and can be passed directly to `createServer` to create a server that serves _only_ files. We want to first check for requests that we should handle specially, though, so we wrap it in another function.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_A9joeSjy6R)const {createServer} = require("http"); const Router = require("./router"); const ecstatic = require("ecstatic"); const router = new Router(); const defaultHeaders = {"Content-Type": "text/plain"}; class SkillShareServer { constructor(talks) { this.talks = talks; this.version = 0; this.waiting = []; let fileServer = ecstatic({root: "./public"}); this.server = createServer((request, response) => { let resolved = router.resolve(this, request); if (resolved) { resolved.catch(error => { if (error.status != null) return error; return {body: String(error), status: 500}; }).then(({body, status = 200, headers = defaultHeaders}) => { response.writeHead(status, headers); response.end(body); }); } else { fileServer(request, response); } }); } start(port) { this.server.listen(port); } stop() { this.server.close(); } }

[](https://eloquentjavascript.net/21_skillsharing.html#p_Blj5l5Ag0w)This uses a similar convention as the file server from the [previous chapter](https://eloquentjavascript.net/20_node.html) for responses—handlers return promises that resolve to objects describing the response. It wraps the server in an object that also holds its state.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_soh9hQbmUg)Talks as resources

[](https://eloquentjavascript.net/21_skillsharing.html#p_oXflSizgmM)The talks that have been proposed are stored in the `talks` property of the server, an object whose property names are the talk titles. These will be exposed as HTTP resources under `/talks/[title]`, so we need to add handlers to our router that implement the various methods that clients can use to work with them.

[](https://eloquentjavascript.net/21_skillsharing.html#p_l/UbmPYgJD)The handler for requests that `GET` a single talk must look up the talk and respond either with the talk’s JSON data or with a 404 error response.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_be1zJWaizQ)const talkPath = /^\/talks\/([^\/]+)$/; router.add("GET", talkPath, async (server, title) => { if (title in server.talks) { return {body: JSON.stringify(server.talks[title]), headers: {"Content-Type": "application/json"}}; } else { return {status: 404, body: `No talk '${title}' found`}; } });

[](https://eloquentjavascript.net/21_skillsharing.html#p_LqiBhzHqti)Deleting a talk is done by removing it from the `talks` object.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_8nIC54r4QK)router.add("DELETE", talkPath, async (server, title) => { if (title in server.talks) { delete server.talks[title]; server.updated(); } return {status: 204}; });

[](https://eloquentjavascript.net/21_skillsharing.html#p_d6iqwIBRHE)The `updated` method, which we will define [later](https://eloquentjavascript.net/21_skillsharing.html#updated), notifies waiting long polling requests about the change.

[](https://eloquentjavascript.net/21_skillsharing.html#p_YlPCGXS+RR)To retrieve the content of a request body, we define a function called `readStream`, which reads all content from a readable stream and returns a promise that resolves to a string.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_ZF0BYHe7yQ)function readStream(stream) { return new Promise((resolve, reject) => { let data = ""; stream.on("error", reject); stream.on("data", chunk => data += chunk.toString()); stream.on("end", () => resolve(data)); }); }

[](https://eloquentjavascript.net/21_skillsharing.html#p_nKzpVkDH6v)One handler that needs to read request bodies is the `PUT` handler, which is used to create new talks. It has to check whether the data it was given has `presenter` and `summary` properties, which are strings. Any data coming from outside the system might be nonsense, and we don’t want to corrupt our internal data model or crash when bad requests come in.

[](https://eloquentjavascript.net/21_skillsharing.html#p_vLKX/LDu2A)If the data looks valid, the handler stores an object that represents the new talk in the `talks` object, possibly overwriting an existing talk with this title, and again calls `updated`.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_C274CtJA7L)router.add("PUT", talkPath, async (server, title, request) => { let requestBody = await readStream(request); let talk; try { talk = JSON.parse(requestBody); } catch (_) { return {status: 400, body: "Invalid JSON"}; } if (!talk || typeof talk.presenter != "string" || typeof talk.summary != "string") { return {status: 400, body: "Bad talk data"}; } server.talks[title] = {title, presenter: talk.presenter, summary: talk.summary, comments: []}; server.updated(); return {status: 204}; });

[](https://eloquentjavascript.net/21_skillsharing.html#p_5d2itdrhai)Adding a comment to a talk works similarly. We use `readStream` to get the content of the request, validate the resulting data, and store it as a comment when it looks valid.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_Wnh7sKEOny)router.add("POST", /^\/talks\/([^\/]+)\/comments$/, async (server, title, request) => { let requestBody = await readStream(request); let comment; try { comment = JSON.parse(requestBody); } catch (_) { return {status: 400, body: "Invalid JSON"}; } if (!comment || typeof comment.author != "string" || typeof comment.message != "string") { return {status: 400, body: "Bad comment data"}; } else if (title in server.talks) { server.talks[title].comments.push(comment); server.updated(); return {status: 204}; } else { return {status: 404, body: `No talk '${title}' found`}; } });

[](https://eloquentjavascript.net/21_skillsharing.html#p_offphkhUrd)Trying to add a comment to a nonexistent talk returns a 404 error.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_gPETZjVKK3)Long polling support

[](https://eloquentjavascript.net/21_skillsharing.html#p_9djdnDsKLr)The most interesting aspect of the server is the part that handles long polling. When a `GET` request comes in for `/talks`, it may be either a regular request or a long polling request.

[](https://eloquentjavascript.net/21_skillsharing.html#p_jwvB6KBzkt)There will be multiple places in which we have to send an array of talks to the client, so we first define a helper method that builds up such an array and includes an `ETag` header in the response.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_BTPI8ewSOP)SkillShareServer.prototype.talkResponse = function() { let talks = []; for (let title of Object.keys(this.talks)) { talks.push(this.talks[title]); } return { body: JSON.stringify(talks), headers: {"Content-Type": "application/json", "ETag": `"${this.version}"`, "Cache-Control": "no-store"} }; };

[](https://eloquentjavascript.net/21_skillsharing.html#p_duw+ZGLY6I)The handler itself needs to look at the request headers to see whether `If-None-Match` and `Prefer` headers are present. Node stores headers, whose names are specified to be case insensitive, under their lowercase names.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_/t9cPK34U3)router.add("GET", /^\/talks$/, async (server, request) => { let tag = /"(.*)"/.exec(request.headers["if-none-match"]); let wait = /wait=(\d+)/.exec(request.headers["prefer"]); if (!tag || tag[1] != server.version) { return server.talkResponse(); } else if (!wait) { return {status: 304}; } else { return server.waitForChanges(Number(wait[1])); } });

[](https://eloquentjavascript.net/21_skillsharing.html#p_MLffXg9p/D)If no tag was given or a tag was given that doesn’t match the server’s current version, the handler responds with the list of talks. If the request is conditional and the talks did not change, we consult the `Prefer` header to see whether we should delay the response or respond right away.

[](https://eloquentjavascript.net/21_skillsharing.html#p_YauV3/x5ZF)Callback functions for delayed requests are stored in the server’s `waiting` array so that they can be notified when something happens. The `waitForChanges` method also immediately sets a timer to respond with a 304 status when the request has waited long enough.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_4a/A2U+gT3)SkillShareServer.prototype.waitForChanges = function(time) { return new Promise(resolve => { this.waiting.push(resolve); setTimeout(() => { if (!this.waiting.includes(resolve)) return; this.waiting = this.waiting.filter(r => r != resolve); resolve({status: 304}); }, time * 1000); }); };

[](https://eloquentjavascript.net/21_skillsharing.html#p_NwQeYwTIHL)Registering a change with `updated` increases the `version` property and wakes up all waiting requests.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_mZ7p2D8VNW)SkillShareServer.prototype.updated = function() { this.version++; let response = this.talkResponse(); this.waiting.forEach(resolve => resolve(response)); this.waiting = []; };

[](https://eloquentjavascript.net/21_skillsharing.html#p_ts7X+FFBfd)That concludes the server code. If we create an instance of `SkillShareServer` and start it on port 8000, the resulting HTTP server serves files from the `public` subdirectory alongside a talk-managing interface under the `/talks` URL.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_7jK2W+D0gW)new SkillShareServer(Object.create(null)).start(8000);

## [](https://eloquentjavascript.net/21_skillsharing.html#h_+jMNtbJ4U3)The client

[](https://eloquentjavascript.net/21_skillsharing.html#p_wVvjBUA/vN)The client-side part of the skill-sharing website consists of three files: a tiny HTML page, a style sheet, and a JavaScript file.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_n3OM6EV/KR)HTML

[](https://eloquentjavascript.net/21_skillsharing.html#p_jNP5xbaXQN)It is a widely used convention for web servers to try to serve a file named `index.html` when a request is made directly to a path that corresponds to a directory. The file server module we use, `ecstatic`, supports this convention. When a request is made to the path `/`, the server looks for the file `./public/index.html` (`./public` being the root we gave it) and returns that file if found.

[](https://eloquentjavascript.net/21_skillsharing.html#p_5cbPKwBv5A)Thus, if we want a page to show up when a browser is pointed at our server, we should put it in `public/index.html`. This is our index file:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_ysNDoq7Ue1)<!doctype html> <meta charset="utf-8"> <title>Skill Sharing</title> <link rel="stylesheet" href="skillsharing.css"> <h1>Skill Sharing</h1> <script src="skillsharing_client.js"></script>

[](https://eloquentjavascript.net/21_skillsharing.html#p_SWRzN1Sl4k)It defines the document title and includes a style sheet, which defines a few styles to, among other things, make sure there is some space between talks.

[](https://eloquentjavascript.net/21_skillsharing.html#p_3zo7gVuOSx)At the bottom, it adds a heading at the top of the page and loads the script that contains the client-side application.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_w81jalhbIM)Actions

[](https://eloquentjavascript.net/21_skillsharing.html#p_bEYXHSjNDU)The application state consists of the list of talks and the name of the user, and we’ll store it in a `{talks, user}` object. We don’t allow the user interface to directly manipulate the state or send off HTTP requests. Rather, it may emit _actions_ that describe what the user is trying to do.

[](https://eloquentjavascript.net/21_skillsharing.html#p_SosAiIHoii)The `handleAction` function takes such an action and makes it happen. Because our state updates are so simple, state changes are handled in the same function.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_JJtzZxGbIS)function handleAction(state, action) { if (action.type == "setUser") { localStorage.setItem("userName", action.user); return Object.assign({}, state, {user: action.user}); } else if (action.type == "setTalks") { return Object.assign({}, state, {talks: action.talks}); } else if (action.type == "newTalk") { fetchOK(talkURL(action.title), { method: "PUT", headers: {"Content-Type": "application/json"}, body: JSON.stringify({ presenter: state.user, summary: action.summary }) }).catch(reportError); } else if (action.type == "deleteTalk") { fetchOK(talkURL(action.talk), {method: "DELETE"}) .catch(reportError); } else if (action.type == "newComment") { fetchOK(talkURL(action.talk) + "/comments", { method: "POST", headers: {"Content-Type": "application/json"}, body: JSON.stringify({ author: state.user, message: action.message }) }).catch(reportError); } return state; }

[](https://eloquentjavascript.net/21_skillsharing.html#p_Uq1nPxr4CD)We’ll store the user’s name in `localStorage` so that it can be restored when the page is loaded.

[](https://eloquentjavascript.net/21_skillsharing.html#p_VcQ5L8zOm7)The actions that need to involve the server make network requests, using `fetch`, to the HTTP interface described earlier. We use a wrapper function, `fetchOK`, which makes sure the returned promise is rejected when the server returns an error code.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_IM58YE2b7h)function fetchOK(url, options) { return fetch(url, options).then(response => { if (response.status < 400) return response; else throw new Error(response.statusText); }); }

[](https://eloquentjavascript.net/21_skillsharing.html#p_c9CWzDQBPu)This helper function is used to build up a URL for a talk with a given title.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_KDfsRI9rOO)function talkURL(title) { return "talks/" + encodeURIComponent(title); }

[](https://eloquentjavascript.net/21_skillsharing.html#p_XrBnpVU/Qd)When the request fails, we don’t want to have our page just sit there, doing nothing without explanation. So we define a function called `reportError`, which at least shows the user a dialog that tells them something went wrong.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_upWq63EA/j)function reportError(error) { alert(String(error)); }

### [](https://eloquentjavascript.net/21_skillsharing.html#i_C2L6BWc+wz)Rendering components

[](https://eloquentjavascript.net/21_skillsharing.html#p_dpJwa0vSxW)We’ll use an approach similar to the one we saw in [Chapter 19](https://eloquentjavascript.net/19_paint.html), splitting the application into components. But since some of the components either never need to update or are always fully redrawn when updated, we’ll define those not as classes but as functions that directly return a DOM node. For example, here is a component that shows the field where the user can enter their name:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_XPxLoKIFvt)function renderUserField(name, dispatch) { return elt("label", {}, "Your name: ", elt("input", { type: "text", value: name, onchange(event) { dispatch({type: "setUser", user: event.target.value}); } })); }

[](https://eloquentjavascript.net/21_skillsharing.html#p_7YLRsTB4aw)The `elt` function used to construct DOM elements is the one we used in [Chapter 19](https://eloquentjavascript.net/19_paint.html).

[](https://eloquentjavascript.net/21_skillsharing.html#p_cYex6IZjTT)A similar function is used to render talks, which include a list of comments and a form for adding a new comment.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_VdTnp45oFj)function renderTalk(talk, dispatch) { return elt( "section", {className: "talk"}, elt("h2", null, talk.title, " ", elt("button", { type: "button", onclick() { dispatch({type: "deleteTalk", talk: talk.title}); } }, "Delete")), elt("div", null, "by ", elt("strong", null, talk.presenter)), elt("p", null, talk.summary), ...talk.comments.map(renderComment), elt("form", { onsubmit(event) { event.preventDefault(); let form = event.target; dispatch({type: "newComment", talk: talk.title, message: form.elements.comment.value}); form.reset(); } }, elt("input", {type: "text", name: "comment"}), " ", elt("button", {type: "submit"}, "Add comment"))); }

[](https://eloquentjavascript.net/21_skillsharing.html#p_uhHeAEhpd6)The `"submit"` event handler calls `form.reset` to clear the form’s content after creating a `"newComment"` action.

[](https://eloquentjavascript.net/21_skillsharing.html#p_mCtWt0pni3)When creating moderately complex pieces of DOM, this style of programming starts to look rather messy. There’s a widely used (non-standard) JavaScript extension called _JSX_ that lets you write HTML directly in your scripts, which can make such code prettier (depending on what you consider pretty). Before you can actually run such code, you have to run a program on your script to convert the pseudo-HTML into JavaScript function calls much like the ones we use here.

[](https://eloquentjavascript.net/21_skillsharing.html#p_1RkCjc7z/I)Comments are simpler to render.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_N9+wrVgBuY)function renderComment(comment) { return elt("p", {className: "comment"}, elt("strong", null, comment.author), ": ", comment.message); }

[](https://eloquentjavascript.net/21_skillsharing.html#p_GWokCP1lhY)Finally, the form that the user can use to create a new talk is rendered like this:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_CrmrTqBxyk)function renderTalkForm(dispatch) { let title = elt("input", {type: "text"}); let summary = elt("input", {type: "text"}); return elt("form", { onsubmit(event) { event.preventDefault(); dispatch({type: "newTalk", title: title.value, summary: summary.value}); event.target.reset(); } }, elt("h3", null, "Submit a Talk"), elt("label", null, "Title: ", title), elt("label", null, "Summary: ", summary), elt("button", {type: "submit"}, "Submit")); }

### [](https://eloquentjavascript.net/21_skillsharing.html#i_QESJMin8/J)Polling

[](https://eloquentjavascript.net/21_skillsharing.html#p_MAgZ8zA1qk)To start the app we need the current list of talks. Since the initial load is closely related to the long polling process—the `ETag` from the load must be used when polling—we’ll write a function that keeps polling the server for `/talks` and calls a callback function when a new set of talks is available.
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_y9uqyFVtpt)async function pollTalks(update) { let tag = undefined; for (;;) { let response; try { response = await fetchOK("/talks", { headers: tag && {"If-None-Match": tag, "Prefer": "wait=90"} }); } catch (e) { console.log("Request failed: " + e); await new Promise(resolve => setTimeout(resolve, 500)); continue; } if (response.status == 304) continue; tag = response.headers.get("ETag"); update(await response.json()); } }

[](https://eloquentjavascript.net/21_skillsharing.html#p_LBeWEgbSva)This is an `async` function so that looping and waiting for the request is easier. It runs an infinite loop that, on each iteration, retrieves the list of talks—either normally or, if this isn’t the first request, with the headers included that make it a long polling request.

[](https://eloquentjavascript.net/21_skillsharing.html#p_4wGPaNuukd)When a request fails, the function waits a moment and then tries again. This way, if your network connection goes away for a while and then comes back, the application can recover and continue updating. The promise resolved via `setTimeout` is a way to force the `async` function to wait.

[](https://eloquentjavascript.net/21_skillsharing.html#p_hPYul5CaBK)When the server gives back a 304 response, that means a long polling request timed out, so the function should just immediately start the next request. If the response is a normal 200 response, its body is read as JSON and passed to the callback, and its `ETag` header value is stored for the next iteration.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_bxOeMBlEZu)The application

[](https://eloquentjavascript.net/21_skillsharing.html#p_AhQIfiK0Gw)The following component ties the whole user interface together:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_PzYGJXojtl)class SkillShareApp { constructor(state, dispatch) { this.dispatch = dispatch; this.talkDOM = elt("div", {className: "talks"}); this.dom = elt("div", null, renderUserField(state.user, dispatch), this.talkDOM, renderTalkForm(dispatch)); this.syncState(state); } syncState(state) { if (state.talks != this.talks) { this.talkDOM.textContent = ""; for (let talk of state.talks) { this.talkDOM.appendChild( renderTalk(talk, this.dispatch)); } this.talks = state.talks; } } }

[](https://eloquentjavascript.net/21_skillsharing.html#p_eC+tHNKRrV)When the talks change, this component redraws all of them. This is simple but also wasteful. We’ll get back to that in the exercises.

[](https://eloquentjavascript.net/21_skillsharing.html#p_i8K8y4/q6h)We can start the application like this:
    
    [](https://eloquentjavascript.net/21_skillsharing.html#c_6Z6pm4dZOv)function runApp() { let user = localStorage.getItem("userName") || "Anon"; let state, app; function dispatch(action) { state = handleAction(state, action); app.syncState(state); } pollTalks(talks => { if (!app) { state = {user, talks}; app = new SkillShareApp(state, dispatch); document.body.appendChild(app.dom); } else { dispatch({type: "setTalks", talks}); } }).catch(reportError); } runApp();

[](https://eloquentjavascript.net/21_skillsharing.html#p_rkcICOffJa)If you run the server and open two browser windows for [_http://localhost:8000_](http://localhost:8000/) next to each other, you can see that the actions you perform in one window are immediately visible in the other.

## [](https://eloquentjavascript.net/21_skillsharing.html#h_TcUD2vzyMe)Exercises

[](https://eloquentjavascript.net/21_skillsharing.html#p_d53G5uBJj7)The following exercises will involve modifying the system defined in this chapter. To work on them, make sure you download the code first ([_https://eloquentjavascript.net/code/skillsharing.zip_](https://eloquentjavascript.net/code/skillsharing.zip)), have Node installed [_https://nodejs.org_](https://nodejs.org), and have installed the project’s dependency with `npm install`.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_QcUCZfnLE+)Disk persistence

[](https://eloquentjavascript.net/21_skillsharing.html#p_wtP8pzYaoa)The skill-sharing server keeps its data purely in memory. This means that when it crashes or is restarted for any reason, all talks and comments are lost.

[](https://eloquentjavascript.net/21_skillsharing.html#p_3H2K0biSmc)Extend the server so that it stores the talk data to disk and automatically reloads the data when it is restarted. Do not worry about efficiency—do the simplest thing that works.

### [](https://eloquentjavascript.net/21_skillsharing.html#i_oMIXw3b5pk)Comment field resets

[](https://eloquentjavascript.net/21_skillsharing.html#p_ZLgsWCWv6a)The wholesale redrawing of talks works pretty well because you usually can’t tell the difference between a DOM node and its identical replacement. But there are exceptions. If you start typing something in the comment field for a talk in one browser window and then, in another, add a comment to that talk, the field in the first window will be redrawn, removing both its content and its focus.

[](https://eloquentjavascript.net/21_skillsharing.html#p_aSyB2z5gLz)In a heated discussion, where multiple people are adding comments at the same time, this would be annoying. Can you come up with a way to solve it?

[◀](https://eloquentjavascript.net/20_node.html) [◆](https://eloquentjavascript.net/index.html)
