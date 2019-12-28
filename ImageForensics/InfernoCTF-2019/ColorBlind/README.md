<h1>Color Blind</h1>

![Screenshot from 2019-12-28 23-30-28](https://user-images.githubusercontent.com/46676598/71547750-32c31600-29ca-11ea-9fb3-9351c042177c.png)

Given an Image,after a quick research I found that it is an image with 64x1 size.Which is soo Weird.


``
~/Downloads$ file colorblind.png <br/>
colorblind.png: PNG image data, 64 x 1, 8-bit/color RGB, non-interlaced
``

<h4>Exploit.py</h4>

```
from PIL import Image

im = Image.open("/home/mindfreaker/Downloads/colorblind.png")
data = list(im.getdata())

flag = ""
for i in data:
	flag+=chr(i[0])
	flag+=chr(i[1])
	flag+=chr(i[2])

print (flag)
```
<h4>./Exploit.py</h4>

``
blahblahblah_hello_how_are_you_today_i_hope_you_are_not_doing_this_manually_infernoCTF{h3y_100k_y0u_4r3_n07_h3x_bl1nD_:O}_doing_this_manually_would_be_a_bad_idea_you_shouldnt_do_it_manually_ok
``

FLAG: `infernoCTF{h3y_100k_y0u_4r3_n07_h3x_bl1nD_:O}`
