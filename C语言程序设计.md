# 函数
void sum(int begin, int end)
{
  ...
}  
函数原型 
void sum(int begin, int end); 写在开头。  


## 字符串
char *str; //是只读的，不可修改  
char word[]; //可以修改  
char *a[]; // 每一个a[n]中为一个指向某处字符的指针  
int main(int agrc, char const *argv[]); //主函数的两个参数  
单字符串的输入输出  
int putchar(int char);
```c
int main(int argc, char* argv[]){
    int ch;
    while ((ch =  getchar()) != EOF){
        putchar(ch);
    }
    printf("get EOF");
}
```

# 字符串函数  <string.h>
- strlen(const char *s); // 返回s的字符串长度，不包括\0
- strcmp(const char *s1, const char *s2); //比较两个字符串, s1==s2 返回0，不相等的时候返回差值。  
相当于
```c
int mycmp(char* s1, char* s2){
	int idx = 0;
	while(s1[idx] == s2[idx] && s1[idx] != '\0'){
		
		idx ++;
	}
	return s1[idx] - s2[idx];

}
```
或者用指针：
```c
int mycmp(char* s1, char* s2){
	
	while(*s1 == *s2 && *s1 != '\0'){
		
		s1++;
		s2++;
	}
	return *s1 - *s2;

}
```
- strcpy  
复制一个字符串  
char *strcpy(char *dst, const char* src)  
char *dst = (char*)malloc(strlen(src) + 1);
strcpy(dst,src);  
```c
char *mycpy(char* dst, const char* src){
	
	int idx =0;

	while(src[idx]){   // 等同于while(src[idx] != '\0')
		
		dst[idx] = src[idx];
		idx++;

	}
	dst[idx] = '\0';
	return dst;

}
```
指针形式：  
```c
char *mycpy(char* dst, const char* src){

	char *ret = dst;
	while(*src != '\0'){
		*dst = *src;
		dst++;
		src++;
	}
	*dst = '\0';
	return ret;

}
```
* strcat  
`char *strcat(char* s1, char* s2)` 把s2连接（catenate）到s1后面，返回s1
防止溢出： strncat(char* s1, char* s2, size_n)  
同样的strncmp(char* s1, char* s2, size_n), 可以只比较前n个  
* strchr  
`char *strchr(const char *s, int c);`返回字符 c 第一次在字符串 s 中出现的位置返回指针，如果未找到字符 c，则返回 NULL
```c
int main ()
{
   char s[] = "hello";
   char* p = strchr(s,'l');  //单引号l
   printf("%s\n", p);
   // 找第二个l
   p = strchr(p+1, 'l');  // p+1 后变为lo
   printf("%s\n", p);
   
   return(0);
}
```
*strstr 字符串中找字符串  
`char* strstr(char* s, char*s2);`  
`char* strcasestr(char* s, char*s2);`忽略大小写    


# 枚举  
emun 枚举类型的名字{名字0，名字1，...，名字n}， 也可以指定值 {red=1, yello, green=5}

# 结构
```c
// 声明结构类型
struct date
{
	int month;   // 分号
	int day;
	int year;
};  //分号
struct date today;  //定义结构变量today，它的类型是struct date
today.month =03;
today.day =18;
today.year = 2020;
```
或者  
`struct date today = {07,31,2014};` 或者 `struct date today = {.month=7, .year=2014};` 或者`p1 = (struct point){5,10};`相当于`p1.x=5; p1.y=10` 也可以`p1=p2`数组不可以这么做  
取地址`struct date *pDate = &today;`  
## 指向结构的指针  






