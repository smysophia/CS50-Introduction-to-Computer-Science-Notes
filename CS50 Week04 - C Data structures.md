# Week04 - C Data Structures
`realloc(list, 4 * sizeof(int))` reallocate the size and copy the original list. See realloc.c  
## define data type
`typedef <old name> <new name>;`  
`typedef unsigned char byte`  
`typedef char* string`
<br>
## Arrays
* bad insertion, bad deletion, fixed size
* random access
* small size
* easy to sort
## linked list
* easy insertion, easy deletion
* look-up is bad, no random access
* small size
* difficult to sort
```c
    node *list = NULL;  // list is the address of a node
    node *n = malloc(sizeof(node));
    n->number = 1;
    n->next = NULL;
    list = n;  // list points to n
```
## hash table
hash table is an array of buckets and each bucket is a linked list.
* easy insertion, easy deltion
* look up good
* gamut of size
## tries  
* insertion is complex. Deletion is easy
* look up is easy
* look up is fast, already sorted
* rapidly get huge
```c
typedef struct node
{
    int number;
    struct node *left;
    struct node *right;
}
node;

bool search(node *tree)
{
    if (tree == NULL)
        return false;
    else if (50 < tree->number)
        return search(tree->left);
    else if (50 > tree->number)
        return search(tree->right);
    else
        return true;
}
```


