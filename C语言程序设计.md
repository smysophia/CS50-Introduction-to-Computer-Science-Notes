# 函数
void sum(int begin, int end)
{
  ...
}  
函数原型 
void sum(int begin, int end); 写在开头。  


#字符串
char *str; //是只读的，不可修改  
char word[]; //可以修改  
char *a[]; // 每一个a[n]中为一个指向某处字符的指针  
int main(int agrc, char const *argv[]); //主函数的两个参数  
单字符串的输入输出  
int putchar(int c);
```c
int main(int argc, char* argv[]){
    int ch;
    while ((ch =  getchar()) != EOF){
        putchar(ch);
    }
    printf("get EOF");
}
```
字符串函数  <string.h>
- strlen(const char *s); // 返回s的字符串长度，不包括\0
- strcmp(const char *s1, const char *s2); //比较两个字符串






