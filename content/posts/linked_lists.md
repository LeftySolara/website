---
title: "Linked Lists"
series: ["Data Structures and Algorithms"]
categories: ["programming", "software development"]
tags: ["dsa", "programming"]
date: 2022-03-28T21:27:39-04:00
draft: false
---

Here we will briefly discuss linked lists, what they are, and when to use them.

## What is a linked list?

A **linked list** is a linear collection of data elements. It consists of a number of **nodes** which represent a sequence. Unlike arrays, data in a linked list is not stored contiguously in memory, and the items' placement in memory does not determine their order. Instead, each node in a list contains a reference to the next node in the list.

## Why use them?

Linked lists allow for insertion and removal of data without having to reallocate or reorganize the entire structure. They allow for insertion and removal of nodes at any point in the list with a constant amount of operations. However, random access is not possible; access time in a linked list is linear.

## What are they used for?

Linked lists are one of the simplest and most common data structures. They are often used to implement other data structures (stacks, queues, hash tables, etc.) and are useful when an array-like structure without a fixed size is needed.

## Implementation

### Basic Structure

A linked list can be thought of as a group of nodes that are connected to each other. Each node contains data and a reference to the next node in the list. An implementation in C is displayed below. Note that here we utilize a separate `list` structure to organize our data, but it is also common to work directly with the nodes, without such a structure.

Our list structure consists of three pieces of data: a pointer to the list head, a pointer to the list tail, and the list size. The **head** pointer in a linked list is a reference to its first item. It is not a separate node itself. The **tail** pointer is a reference to the last node in the list. If the list is empty, both are `NULL`. The `size` variable is here for convenience, so that we do not have to manually count the number of items each time we need the size of the list.

```
stuct node {
    int data;
    struct node *next;
}

struct list {
    struct node *head;
    struct node *tail;

    size_t size;
}
```

And here is a representation of what a list looks like:

![](/images/linked_list.jpg)

### Traversal and Accessing Data

**Traversal** is the process of visiting nodes in a linked list. This is usually done to access the data inside nodes. To do this, we create a new pointer to the head of the list and move it using the `next` pointer in each node:

```
struct node *current = list->head;
while (current) {
    // Do something with the node data
    current = current->next;
}
```

The loop will terminate when `current` is `NULL`, which happens when calling `current->next` from the last item in the list.

### Adding Items

To add an item to a linked list we create a new node and connect it to the existing nodes. If the list is empty, then we just set the head and tail to point to the new node. Otherwise, we traverse the list and add the node. Here is an example of adding a node to the end of a list:

```
/**
 * @brief Add an item to the end of a list
 *
 * @param list The list to add the new node to
 * @param value The value of the item to add to the list
 */
void list_push_back(struct list *list, int value)
{
    /* The list is NULL */
    if (!list) {
        return;
    }

    /* Create the new node */
    struct node *new_node = malloc(sizeof(*new_node));
    new_node->data = value;
    new_node->next = NULL;

    /* Connect the new node to the list */
    if (!list->head) {
        /* The list is empty */
        list->head = new_node;
        list->tail = new_node;
    }
    else {
        struct node *current = list->head;
        while (current->next) {
            current = current->next;
        }
        current->next = new_node;
        list->tail = new_node;
    }
    ++list->size;
}
```

Here is an example of adding to the front of a list:

```
/**
 * @brief Add an item to the front of a list
 *
 * @param list The list to add the new node to
 * @param value The value of the item to add to the list
 */
void list_push_front(struct list *list, int value)
{
    if (!list) {
        return;
    }

    /* Create the new node */
    struct node *new_node = malloc(sizeof(*new_node));
    new_node->data = value;
    new_node->next = NULL;

    if (!list->head) {
        /* The list is empty */
        list->head = new_node;
        list->tail = new_node;
    }
    else {
        new_node->next = list->head;
        list->head = new_node;
    }
    ++list->size;
}
```

And here is inserting into the middle of a list:

```
/**
 * @brief Add an item to a specific place in a list
 *
 * @param list The list to add the new item to
 * @param pos The place in the list to add the item
 * @param value The value of the item to add
 */
void list_insert(struct list *list, unsigned int pos, int value)
{
    /* The list is NULL or the requested index is out of bounds */
    if (!list || pos >= list->size) {
        return;
    }

    /* Insert at the front of the list */
    if (pos == 0) {
        list_push_front(list, value);
    }
    else {
        /* Create the new node */
        struct node *new_node = malloc(sizeof(*new_node));
        new_node->data = value;
        new_node->next = NULL;

        struct node *current = list->head;
        for (int i = 0; i < pos - 1; ++i) {
            current = current->next;
        }
        new_node->next = current->next;
        current->next = new_node;
        ++list->size;
    }
}
```

### Removing Items

Removing items from a linked list is slightly more complex than adding them. When removing an item from a list, we must make sure to connect the items before and after the node being removed. Otherwise, the list will be split in two and no longer connected.

Here is an implementation of removing the last item in a list:

```
/**
 * @brief Remove the last item in a list and return its value
 *
 * @param list The list to remove an item from
 * @return int The value of the last item in the list
 */
int list_pop_back(struct list *list)
{
    int value = list->tail->data;

    if (list->size == 1) {
        free(list->head);
        list->head = NULL;
        list->tail = NULL;
    }
    else {
        struct node *current = list->head;
        while (current->next != list->tail) {
            current = current->next;
        }

        free(list->tail);
        list->tail = current;
        list->tail->next = NULL;
    }
    --list->size;

    return value;
}
```

Here is removal from the front of a list:

```
/**
 * @brief Remove the first item in a list and return its value
 *
 * @param list The list to remove an item from
 * @return int The value of the first item in the list
 */
int list_pop_front(struct list *list)
{
    struct node *current = list->head;
    list->head = list->head->next;

    int value = current->data;
    free(current);
    --list->size;

    return value;
}
```

And here is removing from the middle of the list:

```
/**
 * @brief Remove a node at the given index
 *
 * @param list The list to remove an item from
 * @param index The place in the list to remove
 */
void list_erase(struct list *list, unsigned int index)
{
    if (!list || index >= list->size) {
        return;
    }

    if (list->size == 1) {
        free(list->head);
        list->head = NULL;
        list->tail = NULL;
    }
    else {
        if (index == 0) {
            list_pop_front(list);
        }
        else if (index == list->size - 1) {
            list_pop_back(list);
        }
        else {
            struct node *current = list->head;
            for (int i = 0; i < index - 1; ++i) {
                current = current->next;
            }

            struct node *to_delete = current->next;
            current->next = to_delete->next;
            free(to_delete);
            --list->size;
        }
    }
}
```

## Doubly-Linked Lists

A **doubly-linked list** is a linked list in which each node contains a pointer to both the next and the previous node:

```
stuct node {
    int data;
    struct node *next;
    struct node *prev;
}

struct list {
    struct node *head;
    struct node *tail;

    size_t size;
}
```

Adding and removing items in a doubly-linked list is slightly different from a regular linked list (called a **singly-linked list**). Doubly-linked lists also allow us to traverse the list backwards.

## Conclusion

This ends our brief discussion on linked lists. For more detailed information, I recommend the [Wikipedia article on linked lists](https://en.wikipedia.org/wiki/Linked_list).

I hope that the information here was helpful or useful to you in some way. If you have any questions, comments, or corrections please feel free to send me an email at julianne@julianneadams.info.
