# Week2 - C Array
## Array
`type name[size]` def  
`bool truthtable[3] = {false, true, false}` instantiation syntax size3可以省略，or individual element syntax `truthtable[2] =false` 注意没有`truthtable[3]`  
初始化数组  
`int a[]={1,2,3,4,5};`
或者  
`int count[10] = {0};`
等同于  
```c
for (int i=0; i<10; i++){
        count[i] = 0;
    }
 ```
 初始化制定位置赋值  
 `int a[10] = {[1]=2,3,[8]=8};` 意思是，（第0位仍旧是0）第1位等于2，（顺延）第2位等于3，第8位等于8.  
 数组大小 
 `int length = sizeof(a)/sizeof(a[0])`  
 二维数组  
 `int a[3][5]`
 ```c
 for (i=0; i<3;i++){
    for (j=0;j<5;j++){
        printf("a[%d][%d]=%d\n",i,j,a[i][j]);
        }
    }
 ```
 初始化  
 `int a[2][2] = {{1,2},{3,4}};`  
 `int a[2][2] = {[1][1]=1};` 制定a[1][1]为1，其他自动填充为0
 
 

## Search algorithm  
* Linear search: iterate acroo the array from left to right, search for a specified element. O(n) Ω(1)  
* Binary search: to divide and conquer, reducing the search area by half each time, tring to find the target number. O(log n) Ω(1) 
* Selection sort: find the smallest unsorted element and add it to the end of the sorted list. Iterate over n elements of the array and repeat n times. O(n^2) Ω(n^2)  
* Bubble sort: move higher value element to the right and lower value element to the left. If two adjacent elements are not in order, swap them and add one to the swap counter.O(n^2) Ω(n)
* Insertion sort: look at next unsorted element, insert into the sorted portion by shifting the requisite number of element O(n^2) Ω(n)
* Merge sort: sort smaller arrays and combine those array together in sorted order. O(n*log n) Ω(n*log n)

## 实例
* print bar chart for scores (bar2.c)
```c
#include <stdio.h>
#include <cs50.h>

const int COUNT = 3; // def a global variable (constant variable if you like to address)
void chart(int count, int score[]);

int main()
{
    // get scores from user
    int score[COUNT];
    for (int i = 0; i < COUNT; i++)
    {
        score[i] = get_int("score %i:", i+1);
    }

    // chart scores
    chart(COUNT,score);
}

void chart(int count, int score[])
{
    for (int i = 0; i < count; i++)
    {
        for (int j = 0; j < score[i]; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```

或者bar.c
```c
    // chart scores
    for (int i = 0; i <3; i++)
    {
        chart(score[i]);
    }

void chart(int score)
{
    for (int i = 0; i < score; i++)
    {
        printf("#");
    }
    printf("\n");
}
```

* Printing characters in an array of strings
```c
#include <stdio.h>
#include <cs50.h>
#include <string.h>

int main(int argc, string argv[])
{
    for (int i = 0; i < argc; i++)
    {
        for (int j = 0; j < strlen(argv[i]); j++)
        {
            printf("%c\n",argv[i][j]);
        }
        printf("\n");
    }
}
```

