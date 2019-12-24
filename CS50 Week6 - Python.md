# CS50 Week6 - Python
blur an image
```py
from PIL import Image, ImageFilter

before = Image.open("yixiu.jpg")
after = before.filter(ImageFilter.BLUR)
after.save("out.jpg")
```

argv
```py
from sys import argv, exit

if len(argv) != 2:
    print("missing")
    exit(1)
print(f"hello,{argv[1]}")
```

Google ai
```py
import speech_recognition as sr

recognizer = sr.Recognizer()
with sr.Microphone() as source:
    print("say sth:")
    audio = recognizer.listen(source)
print("I heard: ")
print(recognizer.recognize_google(audio))
```

QR Code
```py
import qrcode

image = qrcode.make("https://www.youtube.com/watch?v=fL308_-Kbt0")
image.save("qr.png", "PNG")
```

File read / write
* Read
```py
WORDS = []
with open("large", "r") as file:
    for line in file.readlines():
        WORDS.append(line.rstrip())
 ```
 
 * write
 ```py
 with open('test.txt', 'w') as file:
    file.write('the string you want to write in')
```

CSV file  
`import csv`  
<font color=red>内容</font>
* Read
```py
list=[]
with open('test.csv','r') as file:
    reader = csv.reader(file)
    for row in reader:
        list.append(row)
```
* Write
```py
with open('test.csv', 'r') as file:
    writer = csv.writer(file)
    for row in list:
        writer.writerow(row)
```

* Write in dictionary
```py
with open("registered.csv", "w") as writefile:
    writer = csv.DictWriter(writefile, fieldnames=["name", "dorm"])
    writer.writeheader()
    writer.writerow({"name":"smy", "dorm":"AAA"})
```

* Read in dictionary
```py
with open("registered.csv", "r") as readfile:
    reader = csv.DictReader(readfile)
    for row in reader:
        print(row["name"], row["dorm"])
```

    

