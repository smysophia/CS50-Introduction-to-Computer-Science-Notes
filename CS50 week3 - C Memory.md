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

## pointer  
