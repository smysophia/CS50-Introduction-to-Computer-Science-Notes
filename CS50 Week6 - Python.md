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
