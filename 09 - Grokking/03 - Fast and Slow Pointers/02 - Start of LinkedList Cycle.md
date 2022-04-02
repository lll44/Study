# [Start of LinkedList Cycle (medium)](https://designgurus.org/path-player?courseid=grokking-the-coding-interview&unit=grokking-the-coding-interview_1628743554403_14Unit)//

## Problem Statement



Given the head of a Singly LinkedList that contains a cycle, write a function to find the starting node of the cycle.

![](https://lwfiles.mycourse.app/systemdesign-public/d8e4b90da04fdc02de3ff530e808e1b2.png)

##

Solution

  

If we know the length of the LinkedList cycle, we can find the start of the cycle through the following steps:

  1. Take two pointers. Let’s call them `pointer1` and `pointer2`.
  2. Initialize both pointers to point to the start of the LinkedList.
  3. We can find the length of the LinkedList cycle using the approach discussed in  LinkedList Cycle. Let’s assume that the length of the cycle is ‘K’ nodes.
  4. Move `pointer2` ahead by ‘K’ nodes.
  5. Now, keep incrementing `pointer1` and `pointer2` until they both meet.
  6. As `pointer2` is ‘K’ nodes ahead of `pointer1`, which means, `pointer2` must have completed one loop in the cycle when both pointers meet. Their meeting point will be the start of the cycle.

Let’s visually see this with the above-mentioned Example-1:

![](https://lwfiles.mycourse.app/systemdesign-public/601ce24e00bd2fe8341dfa1c6345b6ed.png)

We can use the algorithm discussed in LinkedList Cycle to find the length of the cycle and then follow the above-mentioned steps to find the start of the cycle.

##

  

##

Code  

  

Here is what our algorithm will look like:

Java  

class ListNode {

int value = 0;

ListNode next;

  

ListNode(int value) {

this.value = value;

}

}

  

class LinkedListCycleStart {

  

public static ListNode findCycleStart(ListNode head) {

int cycleLength = 0;

// find the LinkedList cycle

ListNode slow = head;

ListNode fast = head;

while (fast != null && fast.next != null) {

fast = fast.next.next;

slow = slow.next;

if (slow == fast) { // found the cycle

cycleLength = calculateCycleLength(slow);

break;

}

}

  

return findStart(head, cycleLength);

}

  

private static int calculateCycleLength(ListNode slow) {

ListNode current = slow;

int cycleLength = 0;

do {

current = current.next;

cycleLength++;

} while (current != slow);

return cycleLength;

}

  

private static ListNode findStart(ListNode head, int cycleLength) {

ListNode pointer1 = head, pointer2 = head;

// move pointer2 ahead 'cycleLength' nodes

while (cycleLength > 0) {

pointer2 = pointer2.next;

cycleLength--;

}

  

// increment both pointers until they meet at the start of the cycle

while (pointer1 != pointer2) {

pointer1 = pointer1.next;

pointer2 = pointer2.next;

}

  

return pointer1;

}

  

public static void main(String[] args) {

ListNode head = new ListNode(1);

head.next = new ListNode(2);

head.next.next = new ListNode(3);

head.next.next.next = new ListNode(4);

head.next.next.next.next = new ListNode(5);

head.next.next.next.next.next = new ListNode(6);

  

head.next.next.next.next.next.next = head.next.next;

System.out.println("LinkedList cycle start: " +

LinkedListCycleStart.findCycleStart(head).value);

  

head.next.next.next.next.next.next = head.next.next.next;

System.out.println("LinkedList cycle start: " +

LinkedListCycleStart.findCycleStart(head).value);

  

head.next.next.next.next.next.next = head;

System.out.println("LinkedList cycle start: " +

LinkedListCycleStart.findCycleStart(head).value);

}

}

  


  


Python3  


from __future__ import print_function

  
  


class Node:

def __init__(self, value, next=None):

self.value = value

self.next = next

  


def print_list(self):

temp = self

while temp is not None:

print(temp.value, end='')

temp = temp.next

print()

  
  


def find_cycle_start(head):

cycle_length = 0

# find the LinkedList cycle

slow, fast = head, head

while (fast is not None and fast.next is not None):

fast = fast.next.next

slow = slow.next

if slow == fast: # found the cycle

cycle_length = calculate_cycle_length(slow)

break

return find_start(head, cycle_length)

  
  


def calculate_cycle_length(slow):

current = slow

cycle_length = 0

while True:

current = current.next

cycle_length += 1

if current == slow:

break

return cycle_length

  
  


def find_start(head, cycle_length):

pointer1 = head

pointer2 = head

# move pointer2 ahead 'cycle_length' nodes

while cycle_length > 0:

pointer2 = pointer2.next

cycle_length -= 1

# increment both pointers until they meet at the start of the cycle

while pointer1 != pointer2:

pointer1 = pointer1.next

pointer2 = pointer2.next

return pointer1

  
  


def main():

head = Node(1)

head.next = Node(2)

head.next.next = Node(3)

head.next.next.next = Node(4)

head.next.next.next.next = Node(5)

head.next.next.next.next.next = Node(6)

  


head.next.next.next.next.next.next = head.next.next

print("LinkedList cycle start: " + str(find_cycle_start(head).value))

  


head.next.next.next.next.next.next = head.next.next.next

print("LinkedList cycle start: " + str(find_cycle_start(head).value))

  


head.next.next.next.next.next.next = head

print("LinkedList cycle start: " + str(find_cycle_start(head).value))

  
  


main()

  


  


C++  


using namespace std;

  


#include <iostream>

  


class ListNode {

public:

int value = 0;

ListNode *next;

  


ListNode(int value) {

this->value = value;

next = nullptr;

}

};

  


class LinkedListCycleStart {

public:

static ListNode *findCycleStart(ListNode *head) {

int cycleLength = 0;

// find the LinkedList cycle

ListNode *slow = head;

ListNode *fast = head;

while (fast != nullptr && fast->next != nullptr) {

fast = fast->next->next;

slow = slow->next;

if (slow == fast) { // found the cycle

cycleLength = calculateCycleLength(slow);

break;

}

}

  


return findStart(head, cycleLength);

}

  


private:

static int calculateCycleLength(ListNode *slow) {

ListNode *current = slow;

int cycleLength = 0;

do {

current = current->next;

cycleLength++;

} while (current != slow);

  


return cycleLength;

}

  


static ListNode *findStart(ListNode *head, int cycleLength) {

ListNode *pointer1 = head, *pointer2 = head;

// move pointer2 ahead 'cycleLength' nodes

while (cycleLength > 0) {

pointer2 = pointer2->next;

cycleLength--;

}

  


// increment both pointers until they meet at the start of the cycle

while (pointer1 != pointer2) {

pointer1 = pointer1->next;

pointer2 = pointer2->next;

}

  


return pointer1;

}

};

  


int main(int argc, char *argv[]) {

ListNode *head = new ListNode(1);

head->next = new ListNode(2);

head->next->next = new ListNode(3);

head->next->next->next = new ListNode(4);

head->next->next->next->next = new ListNode(5);

head->next->next->next->next->next = new ListNode(6);

  


head->next->next->next->next->next->next = head->next->next;

cout << "LinkedList cycle start: " 

<< LinkedListCycleStart::findCycleStart(head)->value << endl;

  


head->next->next->next->next->next->next = head->next->next->next;

cout << "LinkedList cycle start: " 

<< LinkedListCycleStart::findCycleStart(head)->value << endl;

  


head->next->next->next->next->next->next = head;

cout << "LinkedList cycle start: " 

<< LinkedListCycleStart::findCycleStart(head)->value << endl;

}

  


  


JS  


class Node {

constructor(value, next = null) {

this.value = value;

this.next = next;

}

}

  


function find_cycle_start(head) {

cycle_length = 0;

// find the LinkedList cycle

let slow = head,

fast = head;

while ((fast !== null && fast.next !== null)) {

fast = fast.next.next;

slow = slow.next;

if (slow === fast) { // found the cycle

cycle_length = calculate_cycle_length(slow);

break;

}

}

return find_start(head, cycle_length);

}

  
  


function calculate_cycle_length(slow) {

let current = slow,

cycle_length = 0;

while (true) {

current = current.next;

cycle_length += 1;

if (current === slow) {

break;

}

}

return cycle_length;

}

  
  


function find_start(head, cycle_length) {

let pointer1 = head,

pointer2 = head;

// move pointer2 ahead 'cycle_length' nodes

while (cycle_length > 0) {

pointer2 = pointer2.next;

cycle_length -= 1;

}

// increment both pointers until they meet at the start of the cycle

while (pointer1 !== pointer2) {

pointer1 = pointer1.next;

pointer2 = pointer2.next;

}

  


return pointer1;

}

  


const head = new Node(1);

head.next = new Node(2);

head.next.next = new Node(3);

head.next.next.next = new Node(4);

head.next.next.next.next = new Node(5);

head.next.next.next.next.next = new Node(6);

  


head.next.next.next.next.next.next = head.next.next;

console.log(`LinkedList cycle start: ${find_cycle_start(head).value}`);

  


head.next.next.next.next.next.next = head.next.next.next;

console.log(`LinkedList cycle start: ${find_cycle_start(head).value}`);

  


head.next.next.next.next.next.next = head;

console.log(`LinkedList cycle start: ${find_cycle_start(head).value}`);

  


## 

Time Complexity

## 

  
  


As we know, finding the cycle in a LinkedList with ‘N’ nodes and also finding the length of the cycle requires O(N)O(N). Also, as we saw in the above algorithm, we will need O(N)O(N) to find the start of the cycle. Therefore, the overall time complexity of our algorithm will be O(N)O(N).

## 

Space Complexity

## 

  


The algorithm runs in constant space O(1)O(1).
