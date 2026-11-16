C++ DSA Practical – Complete Syntax Guide

📚 Topics Covered

1. Student Database Management
2. Stack Using Array
3. Singly Linked List
4. Binary Search Tree (BST)
5. Graph Traversal (BFS & DFS)
6. Searching Techniques
7. Sorting Algorithms
8. Queue Using Linked List
9. Decimal to Binary Conversion
10. Height and Depth in BST

---

1. Student Database Management

Structure Declaration

struct Student {
    int roll;
    string name;
    float marks, avg;
};

Array of Structures

Student s[50];

Input

cin >> s[i].roll;
cin >> s[i].name;
cin >> s[i].marks;

Display

cout << s[i].roll;
cout << s[i].name;
cout << s[i].marks;

Search by Roll Number

if(s[i].roll == key)
    cout << "Found";

---

2. Stack Using Array

Declaration

int stack[100];
int top = -1;

Push

stack[++top] = value;

Pop

value = stack[top--];

Peek

cout << stack[top];

Overflow

if(top == 99)
    cout << "Overflow";

Underflow

if(top == -1)
    cout << "Underflow";

Display

for(int i=top; i>=0; i--)
    cout << stack[i];

---

3. Singly Linked List

Node Declaration

struct Node {
    int data;
    Node *next;
};

Head Pointer

Node *head = NULL;

Create Node

Node *temp = new Node;
temp->data = value;
temp->next = NULL;

Insert at Beginning

temp->next = head;
head = temp;

Insert at End

while(p->next != NULL)
    p = p->next;

p->next = temp;

Delete from Beginning

temp = head;
head = head->next;
delete temp;

Delete from End

while(p->next->next != NULL)
    p = p->next;

delete p->next;
p->next = NULL;

Display

while(p != NULL) {
    cout << p->data;
    p = p->next;
}

---

4. Binary Search Tree (BST)

Node Declaration

struct Node {
    int data;
    Node *left, *right;
};

Create Node

Node *temp = new Node{value, NULL, NULL};

Insert Node

if(root == NULL)
    root = temp;
else if(x < root->data)
    root->left = insert(root->left, x);
else
    root->right = insert(root->right, x);

Inorder (Left, Root, Right)

inorder(root->left);
cout << root->data;
inorder(root->right);

Preorder (Root, Left, Right)

cout << root->data;
preorder(root->left);
preorder(root->right);

Postorder (Left, Right, Root)

postorder(root->left);
postorder(root->right);
cout << root->data;

Search

if(root == NULL)
    return false;

if(root->data == key)
    return true;

if(key < root->data)
    return search(root->left, key);

return search(root->right, key);

---

5. Graph Traversal (BFS & DFS)

Adjacency Matrix

int graph[10][10];

Visited Array

int visited[10] = {0};

BFS Using Queue

queue<int> q;

q.push(start);
visited[start] = 1;

while(!q.empty()) {
    int v = q.front();
    q.pop();

    cout << v;

    for(int i=0; i<n; i++) {
        if(graph[v][i] && !visited[i]) {
            q.push(i);
            visited[i] = 1;
        }
    }
}

DFS Using Recursion

void DFS(int v) {
    visited[v] = 1;
    cout << v;

    for(int i=0; i<n; i++) {
        if(graph[v][i] && !visited[i])
            DFS(i);
    }
}

---

6. Searching Techniques

Linear Search

for(int i=0; i<n; i++) {
    if(a[i] == key) {
        cout << "Found";
        break;
    }
}

Binary Search

int low = 0, high = n-1;

while(low <= high) {
    int mid = (low + high)/2;

    if(a[mid] == key)
        break;

    else if(key < a[mid])
        high = mid-1;

    else
        low = mid+1;
}

Note: Binary search requires a sorted array.

---

7. Sorting Algorithms

Bubble Sort

for(int i=0; i<n-1; i++) {
    for(int j=0; j<n-i-1; j++) {
        if(a[j] > a[j+1])
            swap(a[j], a[j+1]);
    }
}

Selection Sort

for(int i=0; i<n-1; i++) {
    int min = i;

    for(int j=i+1; j<n; j++) {
        if(a[j] < a[min])
            min = j;
    }

    swap(a[i], a[min]);
}

Insertion Sort

for(int i=1; i<n; i++) {
    int key = a[i];
    int j = i-1;

    while(j>=0 && a[j]>key) {
        a[j+1] = a[j];
        j--;
    }

    a[j+1] = key;
}

---

8. Queue Using Linked List

Node Declaration

struct Node {
    int data;
    Node *next;
};

Front and Rear

Node *front = NULL;
Node *rear = NULL;

Enqueue

Node *temp = new Node{value, NULL};

if(rear == NULL)
    front = rear = temp;

else {
    rear->next = temp;
    rear = temp;
}

Dequeue

if(front != NULL) {
    Node *temp = front;
    front = front->next;
    delete temp;

    if(front == NULL)
        rear = NULL;
}

Display

Node *p = front;

while(p != NULL) {
    cout << p->data;
    p = p->next;
}

---

9. Decimal to Binary Conversion Using Stack

Stack Declaration

stack<int> s;

Push Remainder

while(n > 0) {
    s.push(n % 2);
    n = n / 2;
}

Display Binary

while(!s.empty()) {
    cout << s.top();
    s.pop();
}

Special Case

if(n == 0)
    cout << 0;

---

10. Height and Depth in BST

Height of Tree

int height(Node *root) {
    if(root == NULL)
        return 0;

    return 1 + max(
        height(root->left),
        height(root->right)
    );
}

Depth of Node

int depth(Node *root, int key) {
    int d = 0;

    while(root != NULL) {
        if(root->data == key)
            return d;

        if(key < root->data)
            root = root->left;
        else
            root = root->right;

        d++;
    }

    return -1;
}

---

⭐ Important Basic C++ Syntax

Concept| Syntax
Integer| "int a;"
Float| "float a;"
String| "string name;"
Array| "int a[10];"
Structure| "struct Student {};"
Pointer| "int *p;"
NULL| "NULL"
Dynamic allocation| "new Node;"
Delete memory| "delete p;"
Input| "cin >> a;"
Output| "cout << a;"
If condition| "if(a>b)"
For loop| "for(int i=0;i<n;i++)"
While loop| "while(condition)"
Function| "void display()"
Return| "return 0;"
Swap| "swap(a,b);"
Maximum| "max(a,b);"
Sort| "sort(a,a+n);"

⭐ STL Syntax

Stack

stack<int> s;
s.push(10);
s.pop();
s.top();
s.empty();
s.size();

Queue

queue<int> q;
q.push(10);
q.pop();
q.front();
q.back();
q.empty();

Vector

vector<int> v;
v.push_back(10);
v.pop_back();
v.size();

⭐ Important Viva Questions

Question| Answer
What is Stack?| LIFO
What is Queue?| FIFO
What is Linked List?| Collection of connected nodes
What is BST?| Binary Search Tree
What is BFS?| Breadth First Search
What is DFS?| Depth First Search
Which DS is used in BFS?| Queue
Which DS is used in DFS?| Stack
What is Recursion?| Function calling itself
What is Pointer?| Stores memory address
What is Overflow?| Inserting into a full stack
What is Underflow?| Deleting from an empty stack
What is Inorder?| Left, Root, Right
What is Preorder?| Root, Left, Right
What is Postorder?| Left, Right, Root
Which search needs sorted data?| Binary Search

---

End of C++ DSA Practical Syntax Guide

Made for quick practical revision and viva preparation.
