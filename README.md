# EXP-17

## Aim:
**To Implement Stack Implementation Using Array.**

## Software:
`Microsoft VSCode`

## Theory:
A stack is a linear data structure that follows the Last In First Out (LIFO) principle, meaning that the last element added to the stack is the first one to be removed. It is commonly used in programming for tasks like expression evaluation, backtracking, recursive function calls, and undo operations in editors.

Key Operations in a Stack:
-Push: Adds an element to the top of the stack. -Pop: Removes and returns the top element from the stack. -Peek/Top: Returns the top element without removing it. -isEmpty: Checks if the stack is empty.

Components of Stack Implementation

Top Variable:
The variable top is used to keep track of the index of the top element in the stack. Initially, it is set to -1, indicating an empty stack. After each push operation, top is incremented, and after each pop operation, it is decremented.

Push Operation:
When pushing a new element into the stack, the program checks if the stack has space by comparing top to the maximum size (MAX - 1). If the stack is full, a stack overflow occurs. Otherwise, the new element is added to the array at arr[top + 1], and top is incremented.

Pop Operation:
When removing an element from the stack, the program checks if the stack is empty by checking if top < 0. If the stack is empty, a stack underflow occurs. Otherwise, the top element is returned, and top is decremented.

Peek Operation:
This operation allows viewing the top element without removing it from the stack. If the stack is empty (top < 0), it returns an appropriate message.

Stack Overflow: This occurs when trying to push an element onto a stack that has reached its maximum size. The array is full, and no more elements can be added.

Stack Underflow: This occurs when trying to pop an element from an empty stack. There are no elements left to remove.



## Code: 17A
(A) <br> 
```cpp
// NAME - Kanwaljeet singh
//PRN - 23070123124 
// EXPERIMET - 17(A) 

#include <iostream>
using namespace std;

const int n = 100;
int stack[n], top = -1;

void push(int val) {
    if (top >= n - 1) {
        cout << "Stack overflow" << endl;
    } else {
        stack[++top] = val;
    }
}

void pop() {
    if (top < 0) {
        cout << "Stack underflow" << endl;
    } else {
        cout << "The popped element is: " << stack[top--] << endl;
    }
}

void display() {
    if (top >= 0) {
        cout << "Stack elements are: ";
        for (int i = top; i >= 0; i--) {
            cout << stack[i] << " ";
        }
        cout << endl;
    } else {
        cout << "Stack is empty" << endl;
    }
}

int main()
{
    int ch,val;
    cout<<"1) Push in stack"<<endl;
    cout<<"2) Pop from stack"<<endl;
    cout<<"3) display stack"<<endl;
    cout<<"4) exit"<<endl;

    do
    {
        cout<<"enter choice: "<<endl;
        cin>>ch;
        switch(ch)
        {
            case 1:
            {
                cout<<"enter the value that has to be pushed"<<endl;
                cin>>val;
                push(val);
                break;
            }

            case 2:
            {
                pop();
                break;
            }
            case 3:
            {
                display();
                break;
            }
            case 4:
            {
                cout<<"exit"<<endl;
                break;
            }
            default:
            {
                cout<<"Invalid choice"<<endl;
            }
        }
    }
    while (ch!=4);
    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/4722642c-c087-4388-9b39-c5ba3d50f5de)







## Code: 17B
```cpp
// NAME - Kanwaljeet singh
// PRN - 23070123124
// EXPERIMENT - 17(B) 

#include <iostream>
using namespace std;

#define SIZE 5
#define ERROR -9999

class Stack {
    int top;
    int ar[SIZE];
public:
    Stack() {
        top = -1;
    }
    void push(int num);
    int pop();
    int peak();
    void disp();
};

void Stack::push(int num) {
    if (top == SIZE - 1) {
        cout << "STACK OVERFLOW: STACK IS FULL" << endl;
        return;
    }
    ar[++top] = num;
}

int Stack::pop() {
    if (top == -1) {
        cout << "STACK UNDERFLOW: STACK IS EMPTY" << endl;
        return ERROR;
    }
    return ar[top--];
}

int Stack::peak() {
    if (top == -1) {
        cout << "STACK UNDERFLOW: STACK IS EMPTY" << endl;
        return ERROR;
    }
    return ar[top];
}

void Stack::disp() {
    if (top == -1) {
        cout << "STACK UNDERFLOW: STACK IS EMPTY" << endl;
        return;
    }
    for (int i = 0; i <= top; i++) {
        cout << ar[i] << " ";
    }
    cout << endl;
}

int main() {
    Stack s1;
    s1.push(7);
    s1.push(10);
    s1.push(4);
    
    int val = s1.pop();
    cout << "Popped value: " << val << endl;

    int topValue = s1.peak();
    cout << "Top value: " << topValue << endl;

    cout << "Current stack: ";
    s1.disp();

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/4722642c-c087-4388-9b39-c5ba3d50f5de)


## Code: 17C
```cpp
// NAME - Kanwaljeet singh
// PRN - 23070123124
// EXPERIMENT - 17(C) 

#include <iostream>
using namespace std;
#define size 5
#define error -9999

class stack 
{
    int top, ar[size];

public:
    stack() 
    {
        top = -1;
        ar[0]=0;
    }
    void push(int);
    int pop();
    int peak();
    void disp();
};

void stack::push(int num) 
{
    if (top == size - 1) 
    {
        cout << "Stack overflow: stack is full" << endl;
        return;
    } else 
    {
        ar[++top] = num;
    }
}

int stack::pop() {
    int val;
    if (top == -1) 
    {  // Corrected this line
        cout << "Stack underflow: stack is empty" << endl;
        return error;
    } else 
    {
        val = ar[top--];
        return val;
    }
}

int stack::peak() 
{
    if (top == -1) 
    {
        cout << "Stack underflow: stack is empty" << endl;
        return error;
    } else 
    {
        return ar[top];
    }
}

void stack::disp() 
{
    if (top == -1) 
    {
        cout << "Stack underflow: stack is empty" << endl;
        return;
    } else 
    {
        for (int i = 0; i <= top; i++) 
        {
            cout << ar[i] << " ";
        }
        cout << endl;
    }
}

int main() 
{
    stack s1;
    s1.push(10);
    s1.push(7);
    s1.push(4);
    int val = s1.pop();
    cout << "Popped value: " << val << endl;
    int top = s1.peak();
    cout << "Top value: " << top << endl;
    cout << "Stack contents: ";
    s1.disp();
    return 0;
}
```
## Output:
![image](https://github.com/user-attachments/assets/7d7dc6c3-981d-419f-b156-6be17ae121e5)








### Conclusion:
We learnt the implementation and study of Stack Implementation Using Array.]
