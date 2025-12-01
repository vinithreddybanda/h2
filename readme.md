# Java Linked List Project: Step-by-Step Documentary

This document guides you through creating a simple Java linked list project, managing it with Git and GitHub, branching for feature development, and setting up Jenkins CI for automated builds.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Prerequisites](#prerequisites)
3. [Step 1: Write Java Program (Insert at Beginning)](#step-1-write-java-program-insert-at-beginning)
4. [Step 2: Initialize Git and Push to GitHub](#step-2-initialize-git-and-push-to-github)
5. [Step 3: Create Feature Branch (Insert at End)](#step-3-create-feature-branch-insert-at-end)
6. [Step 4: Set Up Jenkins CI](#step-4-set-up-jenkins-ci)
7. [Conclusion](#conclusion)

---

## Project Overview

This project demonstrates basic linked list operations in Java. You will:
- Implement insertion at the beginning and end of a linked list.
- Use Git for version control and GitHub for remote repository hosting.
- Use branching to manage features.
- Set up Jenkins for continuous integration.

---

## Prerequisites

- **Java** (JDK 8+)
- **Git** (latest version)
- **GitHub account**
- **Jenkins** (installed locally or accessible server)

---

## Step 1: Write Java Program (Insert at Beginning)

Create a new directory for your project and a Java file:

```sh
mkdir LinkedListProject
cd LinkedListProject
notepad LinkedListDemo.java
```

Paste the following code into `LinkedListDemo.java`:

```java
// filepath: LinkedListDemo.java
class Node {
    int data;
    Node next;
    Node(int d) { data = d; next = null; }
}

class LinkedList {
    Node head;

    // Insert at beginning
    public void insertAtBeginning(int data) {
        Node newNode = new Node(data);
        newNode.next = head;
        head = newNode;
    }

    // Display list
    public void printList() {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }
}

public class LinkedListDemo {
    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.insertAtBeginning(10);
        list.insertAtBeginning(20);
        list.insertAtBeginning(30);
        list.printList(); // Output: 30 20 10
    }
}
```

**Test the program:**

```sh
javac LinkedListDemo.java
java LinkedListDemo
```

---

## Step 2: Initialize Git and Push to GitHub

### Initialize Git

```sh
git init
git add LinkedListDemo.java
git commit -m "Initial commit: Insert at beginning"
```

### Create GitHub Repository

1. Go to [GitHub](https://github.com/) and create a new repository (e.g., `LinkedListProject`).
2. Copy the repository URL.

### Add Remote and Push

```sh
git remote add origin https://github.com/<your-username>/LinkedListProject.git
git branch -M main
git push -u origin main
```

---

## Step 3: Create Feature Branch (Insert at End)

### Create and Switch to New Branch

```sh
git checkout -b insert-at-end
```

### Add Insert at End Method

Edit `LinkedListDemo.java`:

```java
// filepath: LinkedListDemo.java
// ...existing code...
    // Insert at end
    public void insertAtEnd(int data) {
        Node newNode = new Node(data);
        if (head == null) {
            head = newNode;
            return;
        }
        Node temp = head;
        while (temp.next != null) {
            temp = temp.next;
        }
        temp.next = newNode;
    }
// ...existing code...

public class LinkedListDemo {
    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.insertAtBeginning(10);
        list.insertAtEnd(40);
        list.insertAtBeginning(20);
        list.insertAtEnd(50);
        list.printList(); // Output: 20 10 40 50
    }
}
// ...existing code...
```

### Commit and Push Branch

```sh
git add LinkedListDemo.java
git commit -m "Add insert at end method"
git push -u origin insert-at-end
```

---

## Step 4: Set Up Jenkins CI

### Install Jenkins

- Download and install Jenkins from [jenkins.io](https://www.jenkins.io/download/).
- Start Jenkins and access it via `http://localhost:8080`.

### Create Jenkins Job

1. **New Item**: Click "New Item", enter a name (e.g., `LinkedListProject`), select "Freestyle project".
2. **Source Code Management**:  
   - Select "Git".
   - Enter your repository URL.
   - Choose branch (`main` or `insert-at-end`).
3. **Build Steps**:  
   - Add "Execute Windows batch command":
     ```sh
     javac LinkedListDemo.java
     java LinkedListDemo
     ```
4. **Save and Build**:  
   - Click "Save".
   - Click "Build Now" to run the job.

### View Build Output

- Click the build number.
- View "Console Output" to see compilation and program output.

---

## Conclusion

You have:
- Built a Java linked list project with insert operations.
- Managed code with Git and GitHub.
- Used branching for feature development.
- Automated builds with Jenkins CI.

This workflow demonstrates modern software development practices for small projects.