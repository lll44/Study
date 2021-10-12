Source 

https://marklodato.github.io/visual-git-guide/index-en.html

# A Visual Git Reference


If the images do not work, you can try the [Non-SVG](https://marklodato.github.io/visual-git-guide/index-en.html?no-svg) version of this page.

This page gives brief, visual reference for the most common commands in git. Once you know a bit about how git works, this site may solidify your understanding. If you're interested in how this site was created, see my [GitHub repository](http://github.com/MarkLodato/visual-git-guide).

Also recommended: [Visualizing Git Concepts with D3](http://onlywei.github.io/explain-git-with-d3/#)

## Contents

  1. [Basic Usage](https://marklodato.github.io/visual-git-guide/index-en.html#basic-usage)
  2. [Conventions](https://marklodato.github.io/visual-git-guide/index-en.html#conventions)
  3. [Commands in Detail](https://marklodato.github.io/visual-git-guide/index-en.html#commands-in-detail)
    1. [Diff](https://marklodato.github.io/visual-git-guide/index-en.html#diff)
    2. [Commit](https://marklodato.github.io/visual-git-guide/index-en.html#commit)
    3. [Checkout](https://marklodato.github.io/visual-git-guide/index-en.html#checkout)
    4. [Committing with a Detached HEAD](https://marklodato.github.io/visual-git-guide/index-en.html#detached)
    5. [Reset](https://marklodato.github.io/visual-git-guide/index-en.html#reset)
    6. [Merge](https://marklodato.github.io/visual-git-guide/index-en.html#merge)
    7. [Cherry Pick](https://marklodato.github.io/visual-git-guide/index-en.html#cherry-pick)
    8. [Rebase](https://marklodato.github.io/visual-git-guide/index-en.html#rebase)
  4. [Technical Notes](https://marklodato.github.io/visual-git-guide/index-en.html#technical-notes)
  5. [Walkthrough: Watching the effect of commands](https://marklodato.github.io/visual-git-guide/index-en.html#appendix-stage)

## Basic Usage

The four commands above copy files between the working directory, the stage (also called the index), and the history (in the form of commits).

  * `git add _files_` copies _files_ (at their current state) to the stage.
  * `git commit` saves a snapshot of the stage as a commit.
  * `git reset -- _files_` unstages files; that is, it copies _files_ from the latest commit to the stage. Use this command to "undo" a `git add _files_`. You can also `git reset` to unstage everything.
  * `git checkout -- _files_` copies _files_ from the stage to the working directory. Use this to throw away local changes.

You can use `git reset -p`, `git checkout -p`, or `git add -p` instead of (or in addition to) specifying particular files to interactively choose which hunks copy.

It is also possible to jump over the stage and check out files directly from the history or commit files without staging first.

  * `git commit -a ` is equivalent to running `git add` on all filenames that existed in the latest commit, and then running `git commit`.
  * `git commit _files_` creates a new commit containing the contents of the latest commit, plus a snapshot of _files_ taken from the working directory. Additionally, _files_ are copied to the stage.
  * `git checkout HEAD -- _files_` copies _files_ from the latest commit to both the stage and the working directory.

## Conventions

In the rest of this document, we will use graphs of the following form.

Commits are shown in green as 5-character IDs, and they point to their parents. Branches are shown in orange, and they point to particular commits. The current branch is identified by the special reference _HEAD_, which is "attached" to that branch. In this image, the five latest commits are shown, with _ed489_ being the most recent. _main_ (the current branch) points to this commit, while _stable_ (another branch) points to an ancestor of _main_'s commit.

## Commands in Detail

### Diff

There are various ways to look at differences between commits. Below are some common examples. Any of these commands can optionally take extra filename arguments that limit the differences to the named files.

### Commit

When you commit, git creates a new commit object using the files from the stage and sets the parent to the current commit. It then points the current branch to this new commit. In the image below, the current branch is _main_. Before the command was run, _main_ pointed to _ed489_. Afterward, a new commit, _f0cec_, was created, with parent _ed489_, and then _main_ was moved to the new commit.

This same process happens even when the current branch is an ancestor of another. Below, a commit occurs on branch _stable_, which was an ancestor of _main_, resulting in _1800b_. Afterward, _stable_ is no longer an ancestor of _main_. To join the two histories, a [merge](https://marklodato.github.io/visual-git-guide/index-en.html#merge) (or [rebase](https://marklodato.github.io/visual-git-guide/index-en.html#rebase)) will be necessary.

Sometimes a mistake is made in a commit, but this is easy to correct with `git commit --amend`. When you use this command, git creates a new commit with the same parent as the current commit. (The old commit will be discarded if nothing else references it.)

A fourth case is committing with a [detached HEAD](https://marklodato.github.io/visual-git-guide/index-en.html#detached), as explained later.

### Checkout

The checkout command is used to copy files from the history (or stage) to the working directory, and to optionally switch branches.

When a filename (and/or `-p`) is given, git copies those files from the given commit to the stage and the working directory. For example, `git checkout HEAD~ foo.c` copies the file `foo.c` from the commit called _HEAD~_ (the parent of the current commit) to the working directory, and also stages it. (If no commit name is given, files are copied from the stage.) Note that the current branch is not changed.

When a filename is _not_ given but the reference is a (local) branch, _HEAD_ is moved to that branch (that is, we "switch to" that branch), and then the stage and working directory are set to match the contents of that commit. Any file that exists in the new commit (_a47c3_ below) is copied; any file that exists in the old commit (_ed489_) but not in the new one is deleted; and any file that exists in neither is ignored.

When a filename is _not_ given and the reference is _not_ a (local) branch — say, it is a tag, a remote branch, a SHA-1 ID, or something like _main~3_ — we get an anonymous branch, called a _detached HEAD_. This is useful for jumping around the history. Say you want to compile version 1.6.6.1 of git. You can `git checkout v1.6.6.1` (which is a tag, not a branch), compile, install, and then switch back to another branch, say `git checkout main`. However, committing works slightly differently with a detached HEAD; this is covered [below](https://marklodato.github.io/visual-git-guide/index-en.html#detached).

### Committing with a Detached HEAD

When _HEAD_ is detached, commits work like normal, except no named branch gets updated. (You can think of this as an anonymous branch.)

Once you check out something else, say _main_, the commit is (presumably) no longer referenced by anything else, and gets lost. Note that after the command, there is nothing referencing _2eecb_.

If, on the other hand, you want to save this state, you can create a new named branch using `git checkout -b _name_`.

### Reset

The reset command moves the current branch to another position, and optionally updates the stage and the working directory. It also is used to copy files from the history to the stage without touching the working directory.

If a commit is given with no filenames, the current branch is moved to that commit, and then the stage is updated to match this commit. If `--hard` is given, the working directory is also updated. If `--soft` is given, neither is updated.

If a commit is not given, it defaults to _HEAD_. In this case, the branch is not moved, but the stage (and optionally the working directory, if `--hard` is given) are reset to the contents of the last commit.

If a filename (and/or `-p`) is given, then the command works similarly to [checkout](https://marklodato.github.io/visual-git-guide/index-en.html#checkout) with a filename, except only the stage (and not the working directory) is updated. (You may also specify the commit from which to take files, rather than _HEAD_.)

### Merge

A merge creates a new commit that incorporates changes from other commits. Before merging, the stage must match the current commit. The trivial case is if the other commit is an ancestor of the current commit, in which case nothing is done. The next most simple is if the current commit is an ancestor of the other commit. This results in a _fast-forward_ merge. The reference is simply moved, and then the new commit is checked out.

Otherwise, a "real" merge must occur. You can choose other strategies, but the default is to perform a "recursive" merge, which basically takes the current commit (_ed489_ below), the other commit (_33104_), and their common ancestor (_b325c_), and performs a [three-way merge](http://en.wikipedia.org/wiki/Three-way_merge). The result is saved to the working directory and the stage, and then a commit occurs, with an extra parent (_33104_) for the new commit. 

### Cherry Pick

The cherry-pick command "copies" a commit, creating a new commit on the current branch with the same message and patch as another commit.

### Rebase

A rebase is an alternative to a [merge](https://marklodato.github.io/visual-git-guide/index-en.html#merge) for combining multiple branches. Whereas a merge creates a single commit with two parents, leaving a non-linear history, a rebase replays the commits from the current branch onto another, leaving a linear history. In essence, this is an automated way of performing several [cherry-pick](https://marklodato.github.io/visual-git-guide/index-en.html#cherry-pick)s in a row.

The above command takes all the commits that exist in _topic_ but not in _main_ (namely _169a6_ and _2c33a_), replays them onto _main_, and then moves the branch head to the new tip. Note that the old commits will be garbage collected if they are no longer referenced.

To limit how far back to go, use the `--onto` option. The following command replays onto _main_ the most recent commits on the current branch since _169a6_ (exclusive), namely _2c33a_.

There is also `git rebase --interactive`, which allows one to do more complicated things than simply replaying commits, namely dropping, reordering, modifying, and squashing commits. There is no obvious picture to draw for this; see [git-rebase(1)](http://www.kernel.org/pub/software/scm/git/docs/git-rebase.html#_interactive_mode) for more details.

## Technical Notes

The contents of files are not actually stored in the index (_.git/index_) or in commit objects. Rather, each file is stored in the object database (_.git/objects_) as a _blob_, identified by its SHA-1 hash. The index file lists the filenames along with the identifier of the associated blob, as well as some other data. For commits, there is an additional data type, a _tree_, also identified by its hash. Trees correspond to directories in the working directory, and contain a list of trees and blobs corresponding to each filename within that directory. Each commit stores the identifier of its top-level tree, which in turn contains all of the blobs and other trees associated with that commit.

If you make a commit using a detached HEAD, the last commit really is referenced by something: the reflog for HEAD. However, this will expire after a while, so the commit will eventually be garbage collected, similar to commits discarded with `git commit --amend` or `git rebase`.

## Walkthrough: Watching the effect of commands

The following walks you through changes to a repository so you can see the effect of the command in real time, similar to how [Visualizing Git Concepts with D3](http://onlywei.github.io/explain-git-with-d3/#) simulates them visually. Hopefully you find this useful.

Start by creating some repository:
    
    $ **git init foo** $ **cd foo** $ **echo 1 > myfile** $ **git add myfile** $ **git commit -m "version 1"** 

Now, define the following functions to help us show information:
    
    show_status() { echo "HEAD: $(git cat-file -p HEAD:myfile)" echo "Stage: $(git cat-file -p :myfile)" echo "Worktree: $(cat myfile)" } initial_setup() { echo 3 > myfile git add myfile echo 4 > myfile show_status } 

Initially, everything is at version 1.
    
    $ **show_status** HEAD: 1 Stage: 1 Worktree: 1 

We can watch the state change as we add and commit.
    
    $ **echo 2 > myfile** $ **show_status** HEAD: 1 Stage: 1 Worktree: 2 $ **git add myfile** $ **show_status** HEAD: 1 Stage: 2 Worktree: 2 $ **git commit -m "version 2"** [main 4156116] version 2 1 file changed, 1 insertion(+), 1 deletion(-) $ **show_status** HEAD: 2 Stage: 2 Worktree: 2 

Now, let's create an initial state where the three are all different.
    
    $ **initial_setup** HEAD: 2 Stage: 3 Worktree: 4 

Let's watch what each command does. You will see that they match the diagrams above.

`git reset -- myfile` copies from HEAD to stage:
    
    $ **initial_setup** HEAD: 2 Stage: 3 Worktree: 4 $ **git reset -- myfile** Unstaged changes after reset: M myfile $ **show_status** HEAD: 2 Stage: 2 Worktree: 4 

`git checkout -- myfile` copies from stage to worktree:
    
    $ **initial_setup** HEAD: 2 Stage: 3 Worktree: 4 $ **git checkout -- myfile** $ **show_status** HEAD: 2 Stage: 3 Worktree: 3 

`git checkout HEAD -- myfile` copies from HEAD to both stage and worktree:
    
    $ **initial_setup** HEAD: 2 Stage: 3 Worktree: 4 $ **git checkout HEAD -- myfile** $ **show_status** HEAD: 2 Stage: 2 Worktree: 2 

`git commit myfile` copies from worktree to both stage and HEAD:
    
    $ **initial_setup** HEAD: 2 Stage: 3 Worktree: 4 $ **git commit myfile -m "version 4"** [main 679ff51] version 4 1 file changed, 1 insertion(+), 1 deletion(-) $ **show_status** HEAD: 4 Stage: 4 Worktree: 4 


