# Data-structures-4

Write a C program to implement a stack using Array and linked List implementation and execute the following operation on stack.
(i)	Push an element into a stack
(ii)	Pop an element from a stack
(iii)	Return the Top most element from  a stack
(iv)	Display the elements in a stack

Algorithm:
Code:

Array Implementation:
#include <stdio.h>
#include <stdlib.h>

#define MAX_SIZE 10

struct ArrayStack {
    int top;
    int array[MAX_SIZE];
};

struct ArrayStack* createArrayStack() {
    struct ArrayStack* stack = (struct ArrayStack*)malloc(sizeof(struct ArrayStack));
    stack->top = -1;
    return stack;
}

int isArrayStackEmpty(struct ArrayStack* stack) {
    return (stack->top == -1);
}

void pushArray(struct ArrayStack* stack, int data) {
    if (stack->top == MAX_SIZE - 1) {
        printf("Stack Overflow\n");
        return;
    }
    stack->array[++stack->top] = data;
}

int popArray(struct ArrayStack* stack) {
    if (isArrayStackEmpty(stack)) {
        printf("Stack Underflow\n");
        return -1;
    }
    return stack->array[stack->top--];
}

int main() {
    struct ArrayStack* arrayStack = createArrayStack();

    // Pushing elements onto the stack
    pushArray(arrayStack, 10);
    pushArray(arrayStack, 20);
    pushArray(arrayStack, 30);

    // Popping elements from the stack
    printf("Popped from arrayStack: %d\n", popArray(arrayStack));
    printf("Popped from arrayStack: %d\n", popArray(arrayStack));
    printf("Popped from arrayStack: %d\n", popArray(arrayStack));

    return 0;
}
Linked List Implementation:

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct LinkedListStack {
    struct Node* top;
};

struct LinkedListStack* createLinkedListStack() {
    struct LinkedListStack* stack = (struct LinkedListStack*)malloc(sizeof(struct LinkedListStack));
    stack->top = NULL;
    return stack;
}

int isLinkedListStackEmpty(struct LinkedListStack* stack) {
    return (stack->top == NULL);
}

void pushLinkedList(struct LinkedListStack* stack, int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = stack->top;
    stack->top = newNode;
}

int popLinkedList(struct LinkedListStack* stack) {
    if (isLinkedListStackEmpty(stack)) {
        printf("Stack Underflow\n");
        return -1;
    }
    struct Node* temp = stack->top;
    int data = temp->data;
    stack->top = temp->next;
    free(temp);
    return data;
}

int main() {
    struct LinkedListStack* linkedListStack = createLinkedListStack();

    // Pushing elements onto the stack
    pushLinkedList(linkedListStack, 40);
    pushLinkedList(linkedListStack, 50);
    pushLinkedList(linkedListStack, 60);

    // Popping elements from the stack
    printf("Popped from linkedListStack: %d\n", popLinkedList(linkedListStack));
    printf("Popped from linkedListStack: %d\n", popLinkedList(linkedListStack));
    printf("Popped from linkedListStack: %d\n", popLinkedList(linkedListStack));

    return 0;
}
OUTPUT :
Stack Menu
1. Push
2. Pop
3. Display
4. Exit
Enter your choice: 1
Enter data to push: 10
10 pushed to stack

Enter your choice: 1
Enter data to push: 20
20 pushed to stack

Enter your choice: 1
Enter data to push: 30
30 pushed to stack

Enter your choice: 3
Elements in stack: 30 20 10 

Enter your choice: 2
Popped element: 30

Enter your choice: 3
Elements in stack: 20 10 

Enter your choice: 2
Popped element: 20

Enter your choice: 2
Popped element: 10

Enter your choice: 2
Stack Underflow

Enter your choice: 3
Stack is empty

Enter your choice: 4
Exiting program
