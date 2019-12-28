<h1>Color Blind</h1>



<h4>Exploit.py</h4>

``<p>
#!/usr/bin/python3

from PIL import Image

im = Image.open("/home/mindfreaker/Downloads/colorblind.png")
data = list(im.getdata())

for i in data:
	print(chr(i[0]),end="")
	print(chr(i[1]),end="")
	print(chr(i[2]),end="")


</p>``
