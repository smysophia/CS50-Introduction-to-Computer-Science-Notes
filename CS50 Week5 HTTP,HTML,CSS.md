# Week5 HTTP,HTML,CSS  
* 32 bit IP(internet protocol) address: IPv4  
* 80 = HTTP(HyperText Transfer Protocol); 25 = SMTP(Email)
* URL(Uniform Resource Locater) is the address of a server. DNS(Domain Name System域名系统)coverts domain name to IP address and vise sersa.
* HTTP/1.1 200 OK Content-type: Text/html  

## HTML  
* html means HyperText Markup Language 超文本标记语言
* <!-- Comment goes here -->
* `<b>boldface</b>` bold `<i>italics</i>` italics `<u>underline</u>` underline 
* unordered list and ordered list:
```html
<ul>
   <li>foo</li>
   <li>bar</li>
   <li>baz</li>
</ul>
<ol start=4>
    <li>4</li>
    <li>6</li>
<\ol>
```
    

```html
<!DOCTYPE html>
<html lang ="en">
    <head>
        <title>
            hello, title
        </title>
    </head>
    <body>
       <strong>Hello</strong>body.
       <image alt = "phto" src = "dan.jpg">
       visit <a href = "https://www.harvard.edu/">Harvard</a>
    </body>
</html>
```

you can check the code: <html> https://validator.w3.org/

## CSS
* CSS(Cascading Style Sheets层叠样式表) 
```css
body
{
    text-align: center;
    background-color: grey;
    color: #ffffff;
    font-family: Arial;
    opacity: 0.8;
}

header
{
    font-size: 20pt;
}

main
{
    font-size: medium;
}

footer
{
    font-size: small;
}
```

`<link href="css.css" rel="sylesheets">` to introduce css in html

## Javascript   

`let counter = 0;`
```js
function greet()
{
    alert("hello world");
}
```

`let name = document.querySelector("#name").value;` a variable called name stores the value of node that has a unique identifier of "name"


