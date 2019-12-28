<h1>Color Blind</h1>

![Screenshot from 2019-12-28 23-30-28](https://user-images.githubusercontent.com/46676598/71547750-32c31600-29ca-11ea-9fb3-9351c042177c.png)

Given an Image,after a quick research I found that it is an image with 64x1 size.Which is soo Weird.


~/Downloads$ file colorblind.png 
colorblind.png: PNG image data, 64 x 1, 8-bit/color RGB, non-interlaced


<h4>Exploit.py</h4>

````
#!/usr/bin/python3

from PIL import Image

im = Image.open("/home/mindfreaker/Downloads/colorblind.png")
data = list(im.getdata())

for i in data:
	print(chr(i[0]),end="")
	print(chr(i[1]),end="")
	print(chr(i[2]),end="")


````
