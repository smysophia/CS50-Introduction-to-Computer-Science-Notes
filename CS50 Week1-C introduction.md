# Week1 - C introduction
## 输入输出
```c
# include <stdio.h>
# include <cs50.h>

int main(void)
{
    string name = get_string("what is your name?\n");
    printf("hello, %s\n", name);
}
```

用get_double提高infinite float准确性(double takes 8 bytes of memory 64 bits)
```c
int main(void)
{
    // use double to get the infinite float number more precise
    double a = get_double("a: ");
    double b = get_double("b: ");
    printf("a/b=%.50f\n", a / b);
}
```

## Condition 
判断奇偶 if
```c
int main(void)
{
    int x = get_int("x:");
    // check parity of integer
    if (x % 2 == 0){
        printf("even\n");
    }
    else{
        printf("odd\n");
    }
}
```

?: 代替简单的if else判断
```c
int main(void){
    int x = get_int("x = ");
    string y = (x % 2 == 0) ? "even\n" : "odd\n";
printf("%s\n", y);
}
```

文字判断if（or） else if
```c
int main(void)
{
    char c = get_char("enter y or n: ");
    if (c == 'y' || c == 'Y')
    {
        printf("YES\n");
    }
    else if (c == 'n' || c == 'N')
    {
        printf("NO\n");
    }
}
```

case conditional statement
```c
 int x = get_int("");
  switch(x)
  {
        case 1:
          printf("one\n");
          break;   // withouth break, the program will runn all case1 case2 and default      
        case 2:
          printf("two\n");
          break;          
        default:
          printf("sorry\n");                     
  }
  ```
 
## loop 
定义函数，循环
```c
// define a function with one input no return value(just print it)
void cough(int n)
{
  for (int i = 0; i < n; i++)
  {
     printf("cough\n");  
  }  
}

int main(void)
{
    int n = get_int("n = ");
    cough(n);
}
```


  
  
  
