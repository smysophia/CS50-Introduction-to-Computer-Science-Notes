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
```c
// 声明结构变量date，同时定义结构变量myday
struct date
{
	int month;   
	int day;
	int year;
}myday;
struct date *p = &myday;  //指向myday的指针p
//相当于(*p).month =12;
p->month =12;
```
将数值通过scanf传入结构
方法一，传出一个结构，赋值给原结构
```c
int main(int argc, char const *argv[])
{
	struct date today = {0,0,0};
	today = getstruct();
	printf("%d,%d,%d\n",today.month, today.day, today.year);
	return 0;
}

struct date getstruct(void){
	struct date p;
	scanf("%d", &p.month);
	scanf("%d", &p.day);
	scanf("%d", &p.year);
	printf("在函数中的%d,%d,%d\n",p.month, p.day, p.year);
	return p;
}
```
方法二，传入指针
```c
#include <stdio.h>
struct date
{
	int month;
	int day;
	int year;
};

struct date* getstruct(struct date *p);
void output (struct date);


int main(int argc, char const *argv[])
{
	struct date today = {0,0,0};
	// case 1
	// getstruct(&today);
	// output(today);
	// case 2
	// output(*getstruct(&today));
	*getstruct(&today) = (struct date){1, 1, 2019};  // *函数getstruct返回的指针，取值
	output(today);
	return 0;
}

struct date* getstruct(struct date *p){  // 传入一个指针到函数getstruct然后返回一个指针
	scanf("%d", &p->month);
	scanf("%d", &p->day);
	scanf("%d", &p->year);
	printf("在函数中的%d,%d,%d\n",p->month, p->day, p->year);
	return p;
}

void output (struct date today){
	printf("在output中%d,%d,%d\n",today.month, today.day, today.year);
}

```
结构数组  
`struct date dates[]={{4,5,2019}, {1,1,2020}}` 数组date内每一个元素是一个结构变量struct date

# 自定义数据类型 typedef  
`typedef int length` 使得length成为int类型的别名
```c
typedef struct ADate{
	int month;
	int day;
	int year;
} Date;  // 给struct Adate取了一个新名字叫Date， 以后Date就可以代表struct ADate
```

# 全局变量
```c
#include <stdio.h>
int gAll =12;  // 全局变量，在所有函数中都可以使用。
int f(void){
	printf("in %s gAll=%d\n", __func__, gAll);  //__func__, 指代当前函数名字
	gAll += 2;
	printf("in %s gAll=%d\n", __func__, gAll);
	return gAll;
}

int main(int argc, char const *argv[])
{
	printf("in %s gAll=%d\n", __func__, gAll);
	f();
	printf("in %s gAll=%d\n", __func__, gAll);
	return 0;
}
```
输出结果：  
in main gAll=12  
in f gAll=12  
in f gAll=14  
in main gAll=14  
  
## 静态本地变量 static 

当函数离开的时候， 静态本地变量回继续存在并保持其值，初始化只会在第一次进入这个函数的时候做，以后进入函数时会保持上次离开时的值。
```c
int f(void){
	static int all = 1;
	printf("in %s all=%d\n", __func__, all);
	all += 2;
	return all;
}

int main(int argc, char const *argv[])
{
	f();
	f();
	f();
	return 0;
}
```
输出结果  
in f all=1  
in f all=3  
in f all=5  
如果不是静态本地变量（去除static），则输出结果  
in f all=1  
in f all=1  
in f all=1  
实际上是特殊的全局变量。  
&gAll= 0x10cff101c  
&all= 0x10cff1018 地址和全局变量在一起。全局生存期，本地作用域。
返回指针的函数  
返回本地变量的地址是危险的，返回全局变量或者静态本地变量的地址是安全的。

# 编译预处理指令
#开头的是编译预处理指令
`#define PI 3.1415`定义一个宏.`#define <名字> <值>` 没有分号，因为不是c语言语句。
多行定义：
```c
#define PRT printf("%f", PI); \
	    printf ("%f\n", PI2)
```
  
指令`$ gcc 1.c --save-temps`保存临时文件  
`ls -l`查看列表  
`tail 1.i`查看代码  

预定义的宏：  
__LINE__  行号   
__FILE__  文件名  
__DATE__  编译的日期  
__TIME__  编译的时间  
__STDC__  判断是不是标准C  
  
函数的宏  
`#defien cube(x) ((x)*(x)*(x))`

# 多个源代码文件  
同一个项目中，函数原型放入头文件以.h结尾，需要调用时#include这个头文件。头文件时预处理的。
全局变量的声明在.h文件中`extern int gAll;`  
用标准头文件结构来保护，免得重复声明。
```c
#ifndef __LIST_HEAD__
#define __LIST_HEAD__
...

#endif
```

# 格式化输入输出  
* printf  %[flag][width][.prec][hlL]type  返回值：输出的字符数（包含一个\n）  
	* flag
		* - 左对齐
		* + 在前面放加或减号（如果是负数就变成减号）
		* （space） 正数留空
		* 0  零填充
	* width 或prec
		* number 最小字符数（要占据多少位）
		* .number 小数点后几位
		* * 下一个参数是字符数
		* .* 下一个参数是小数点后的位数
	* hlL是修饰
	* type
		* i或d int
		* u unsigned int
		* x 十六进制
		* n 已经输出了多少个字符，填到指针里去 `printf("%d%n\n", 12345, &num); printf("%d\n", num);`输出5
* scanf %[flag]type  返回值：读入的项目数
	* flag
		* * 跳过
		* number 最大字符数
	* type
		* d int
		* i 可以为16进制或者8进制的int
		* [...] 所允许的字符

# 文件的输入输出  
`FILE* fopen(const char * restrct path, const char * restrct mode);`打开文件，例如`FILE* fp = fopen("file", "r");`  
* mode
	* r 打开只读
	* r+ 打开读写，从文件头开始
	* w 打开只写，不存在就新建，存在就清空重新写
	* w+ 打开读写，不存在就新建，存在就清空重新写
	* a 打开追加，继续写
	* .x 只新建，如果文件存在则不能打开  

`fscanf(FILE*);`读文件, 例如`fscanf(fp, "%d", &num);` 从打开的fp中读入一个整数  
`fprintf(FILE*);`写文件  
`int fclose(FILE * stream);` 关闭  
