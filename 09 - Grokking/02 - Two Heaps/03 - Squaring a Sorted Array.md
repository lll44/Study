# [Squaring a Sorted Array (easy)](https://designgurus.org/path-player?courseid=grokking-the-coding-interview&unit=grokking-the-coding-interview_1628743435284_3Unit)

  



 
## 

Problem Statement  


  


Given a sorted array, create a new array containing squares of all the numbers of the input array in the sorted order.

Example 1:
    
    Input: [-2, -1, 0, 2, 3]  
    Output: [0, 1, 4, 4, 9]  
    

Example 2:
    
    Input: [-3, -1, 0, 1, 2]  
    Output: [0, 1, 1, 4, 9]  
    

  


## 

Solution

  


This is a straightforward question. The only trick is that we can have negative numbers in the input array, which will make it a bit difficult to generate the output array with squares in sorted order.

An easier approach could be to first find the index of the first non-negative number in the array. After that, we can use Two Pointers to iterate the array. One pointer will move forward to iterate the non-negative numbers, and the other pointer will move backward to iterate the negative numbers. At any step, whichever number gives us a bigger square will be added to the output array. For the above-mentioned Example-1, we will do something like this:

![](https://lwfiles.mycourse.app/systemdesign-public/303fff02d76af64fa2bab1041c5cdb12.png)

Since the numbers at both ends can give us the largest square, an alternate approach could be to use two pointers starting at both ends of the input array. At any step, whichever pointer gives us the bigger square, we add it to the result array and move to the next/previous number according to the pointer. For the above-mentioned Example-1, we will do something like this:

![](https://lwfiles.mycourse.app/systemdesign-public/899c2fc30194465bb9ca25074adf5d02.png)

## 

Code  

  


Here is what our algorithm will look like:

Java  


class SortedArraySquares {

  


public static int[] makeSquares(int[] arr) {

int n = arr.length;

int[] squares = new int[n];

int highestSquareIdx = n - 1;

int left = 0, right = arr.length - 1;

while (left <= right) {

int leftSquare = arr[left] >md.png COPYING Config.plist CopyAsMarkdown-demo.mp4 README.md _Signature.plist html2md.sh html2text.py arr[left];

int rightSquare = arr[right] >md.png COPYING Config.plist CopyAsMarkdown-demo.mp4 README.md _Signature.plist html2md.sh html2text.py arr[right];

if (leftSquare > rightSquare) {

squares[highestSquareIdx--] = leftSquare;

left++;

} else {

squares[highestSquareIdx--] = rightSquare;

right--;

}

}

return squares;

}

  


public static void main(String[] args) {

  


int[] result = SortedArraySquares.makeSquares(new int[] { -2, -1, 0, 2, 3 });

for (int num : result)

System.out.print(num + " ");

System.out.println();

  


result = SortedArraySquares.makeSquares(new int[] { -3, -1, 0, 1, 2 });

for (int num : result)

System.out.print(num + " ");

System.out.println();

}

}

  


  


Python3  


def make_squares(arr):

n = len(arr)

squares = [0 for x in range(n)]

highestSquareIdx = n - 1

left, right = 0, n - 1

while left <= right:

leftSquare = arr[left] >md.png COPYING Config.plist CopyAsMarkdown-demo.mp4 README.md _Signature.plist html2md.sh html2text.py arr[left]

rightSquare = arr[right] >md.png COPYING Config.plist CopyAsMarkdown-demo.mp4 README.md _Signature.plist html2md.sh html2text.py arr[right]

if leftSquare > rightSquare:

squares[highestSquareIdx] = leftSquare

left += 1

else:

squares[highestSquareIdx] = rightSquare

right -= 1

highestSquareIdx -= 1

  


return squares

  
  


def main():

  


print("Squares: " + str(make_squares([-2, -1, 0, 2, 3])))

print("Squares: " + str(make_squares([-3, -1, 0, 1, 2])))

  
  


main()

  


  


C++  


using namespace std;

  


#include <iostream>

#include <vector>

  


class SortedArraySquares {

public:

static vector<int> makeSquares(const vector<int>& arr) {

int n = arr.size();

vector<int> squares(n);

int highestSquareIdx = n - 1;

int left = 0, right = n - 1;

while (left <= right) {

int leftSquare = arr[left] >md.png COPYING Config.plist CopyAsMarkdown-demo.mp4 README.md _Signature.plist html2md.sh html2text.py arr[left];

int rightSquare = arr[right] >md.png COPYING Config.plist CopyAsMarkdown-demo.mp4 README.md _Signature.plist html2md.sh html2text.py arr[right];

if (leftSquare > rightSquare) {

squares[highestSquareIdx--] = leftSquare;

left++;

} else {

squares[highestSquareIdx--] = rightSquare;

right--;

}

}

return squares;

}

};

  


int main(int argc, char* argv[]) {

vector<int> result = SortedArraySquares::makeSquares(vector<int>{-2, -1, 0, 2, 3});

for (auto num : result) {

cout << num << " ";

}

cout << endl;

  


result = SortedArraySquares::makeSquares(vector<int>{-3, -1, 0, 1, 2});

for (auto num : result) {

cout << num << " ";

}

cout << endl;

}

  


JS  


function make_squares(arr) {

const n = arr.length;

squares = Array(n).fill(0);

let highestSquareIdx = n - 1;

let left = 0,

right = n - 1;

while (left <= right) {

let leftSquare = arr[left] >md.png COPYING Config.plist CopyAsMarkdown-demo.mp4 README.md _Signature.plist html2md.sh html2text.py arr[left],

rightSquare = arr[right] >md.png COPYING Config.plist CopyAsMarkdown-demo.mp4 README.md _Signature.plist html2md.sh html2text.py arr[right];

if (leftSquare > rightSquare) {

squares[highestSquareIdx] = leftSquare;

left += 1;

} else {

squares[highestSquareIdx] = rightSquare;

right -= 1;

}

highestSquareIdx -= 1;

}

  


return squares;

}

  
  


console.log(`Squares: ${make_squares([-2, -1, 0, 2, 3])}`);

console.log(`Squares: ${make_squares([-3, -1, 0, 1, 2])}`);

  


  


## 

Time Complexity

## 

  
  


The above algorithm’s time complexity will be O(N)O(N) as we are iterating the input array only once.

## 

Space Complexity

## 

  


The above algorithm’s space complexity will also be O(N)O(N); this space will be used for the output array.
