# Week 3 - C Memorry
## file pointer
`FILE *ptr = fopen("filename", "operation")` filename is a string(char *); open a file, r=read, w=write, a=append  
`fclose(ptr)` close the file  
`char c = fgetc(ptr)` file get a character, pointer must be opened with "r"  
```c
char ch;
while ((ch = fgetc(ptr)) != EOF)  //EOF = End Of File
   printf("%c",ch);
```
`fputc('ch', ptr2)` ptr2 must be opened with w or a  
`fread(<buffer>, <size>, <qty>, <inptr>)` buffer: pointer to a struct that will contain the bytes you're reading; inptr: file pointer `FILE * inptr = fopen("filename", "r")`
 ```c
 int arr[10];
 fread(arr, sizeof(int),10,ptr);
 // or read 80 double
 double *arr2 = malloc(sizeof(double) *80);
 fread(arr2, sizeof(double), 80,ptr)
 // or read one char just like fgetc
 char c;
 fread(&c, sizeof(char),1,ptr);
 ```
 
`fgets()`read a full string form a file.  
`fputs()`wtrite a full string to a file.  
`fprintf()`write a formatted string to a file  
`fseek(inptr,offset,from)`rewind or fast-forward in a file. inptr = the input pointer; offser = num of bytes to move cursur; from = {SEEK_CUR,SEEK_SET,SEEK_END} which means current of position,beginning of the file, end of the file  
`ftell()` at what (byte) position you are
`feof(ptr)`  if(feof(ptr)) break;

## pointer 指针  
`int i; printf("%p\n", &i);` 打印i的地址  
`int *p = &i` p的值是i的地址（p指向i）*p是一个int  
`int k = *p` 访问地址p上的变量  
`*&yptr = *(&yptr) = *(yptr的地址) = yptr地址上的变量 = yptr`  
`&*yptr = &(*yptr) = &(y指针的变量就是y) = &(y) = yptr`  
举例 
分别打印变量和地址
```c
int main(void)
{
    int var[] = {10, 100, 200};
    int *ptr[3];

    for (int i = 0; i < 3; i++)
    {
        ptr[i] = &var[i];  // ptr是赋值为整数的地址
        printf("var[%d] = %d\n", i, var[i]);
        printf("ptr[%d] = %p\n", i, ptr[i]);
    }
}
```

打印的结果
var[0] = 10
ptr[0] = 0x7ffd98dcc930
var[1] = 100
ptr[1] = 0x7ffd98dcc934
var[2] = 200
ptr[2] = 0x7ffd98dcc938
  
举例交换两个数  
```c
void swap(int *pa, int *pb){
   int t = *pa;
   *pa = *pb;
   *pb = t;
}
```
求数列中的最大值和最小值
```c
// 先定义一个函数
void minmax(int a[], int len, int *min, int *max){   // 传入指针min 指针max
    int i;
    *min = *max = a[0];
    for (i=1; i < len; i++){
        if (a[i] < *min){
            *min = a[i];  // a[i]赋值到 min指针上的变量（*min） 上去
        }
        if (a[i] > *max){
            *max = a[i];
        }
    }
}

int main()
{
    int a[] = {1,2,3,6};
    int min, max;
    int len;
    len = sizeof(a) / sizeof(a[0]);

    minmax(a, len, &min, &max);  // 传入 整数min和max的地址(指针) 到函数中去

    printf("min=%d, max=%d\n", min, max);
}
```




## Dynamic memory allocation 动态内存分配  
`#include <stdlib.h>`分配所需的内存空间，并返回一个指向它的指针
`malloc()` returns to a pointer of the memory
```c
// statically obtain an integer
int x;

//dynamically obtain an integer
int *px = mallo(sizeof(int));

// get an integer from the user
int x = get_int();

//array of float on the stack
float stack_array[x];

//array of float on the heap
float* heap_array = malloc(x * sizeof(float))
```
when you finish working wih dynamically allocated momory `free(ptr)`

```c
int m;   //statically declare an integer called m.
int *a;  // statically declare a pointer called a.
int *b = malloc(sizeof(int)); // dynamically give me one int's worth of space
a = &m;   // means a points to m
a = b;   // a and b point to same location. a points to where b currently points to (the dynamically allocated block)
m = 10;
*b = 12; // dereferencing b (travel along the arrow to where b points) put 12 in that location.
free(b); // take the 4 bytes back
```

<img src="https://github.com/smysophia/yixiu/blob/master/Capture.PNG" alt="capture"  width="200" height="250" />

