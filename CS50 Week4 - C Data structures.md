# Week04 - C Data Structures
`realloc(list, 4 * sizeof(int))` reallocate the size and copy the original list. See realloc.c  
`fscanf(file, "%d", &number)` file is a pointer to FILE. &number is a address  
`int strcasecmp (const char *s1, const char *s2)` string case insensitive compare. #include <string.h> 返回值：若参数s1 和s2 字符串相同则返回0。s1 > s2 则返回大于0 的值，s1 < s2 则返回小于0 的值。

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
link the head pointer to a new node.
```c
    node *list = NULL;  // list is the address of a node
    node *n = malloc(sizeof(node));
    n->number = 1;
    n->next = NULL;
    list = n;  // list points to n
```
* First, declaring a linked node
```c
typedef struct node
{
    int value;
    struct node *next;
}
node;
```

* push a node to the beginning of a linked list(see linked.c)
```c
node *pushNode(node *head, int value)
{
    node *new_node = (node*) malloc(sizeof(node));
    new_node->value = value; // if it is a stirng use strcpy()
    new_node->next = head;  // new node poites to the 1st node
    head = new_node;  // head points to the new node
    return head;    // return the struct node pointer head
}
```

* add a node to the end of a linked list
```c
node *addNode(node *head, int value)
{
    node *new_node = (node*) malloc(sizeof(node));
    new_node->value = value;
    new_node->next = NULL;

    //  If the Linked List is empty, then make the new node as head
    if (head == NULL)
    {
        head = new_node;
    }

    // Else traverse till the last node
    else
    {
        node *last = head;
        while (last->next != NULL)
        {
            last = last->next;
        }
        // change last->next to point the new_node
        last->next = new_node;
    }
    return head;
}
```

* check (compare) the value wether in the linked list
```c
// Returns true if word is in dictionary else false
bool check(const char *word)
{

    node *cursor = hashtable[hash(word)];
    while (cursor != NULL)
    {
        if (strcasecmp(word, cursor->word) == 0)  // compare string to string. if equal, returns 0
            return true;
        
        else
            cursor = cursor->next;
    }
    return false;
}
```


* print the linked list
```c
void printList(node *head)
{
    while(head != NULL)
    {
        printf("num= %i\n", head->value);
        head = head->next;
    }
}
```

* last free all memory
```c
void destroy(node *head)
{
    node *cursor = head;

    while (cursor != NULL)
    {
        node *temp = cursor;
        cursor = cursor->next;
        free(temp);
    }
}
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


