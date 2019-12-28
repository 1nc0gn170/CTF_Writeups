<h1>Color Blind</h1>

![Screenshot from 2019-12-28 23-30-28](https://user-images.githubusercontent.com/46676598/71547750-32c31600-29ca-11ea-9fb3-9351c042177c.png)

Given an Image,after a quick research I found that it is an image with 64x1 size.Which is soo Weird.


```
~/Downloads$ file colorblind.png 

colorblind.png: PNG image data, 64 x 1, 8-bit/color RGB, non-interlaced
```
<br/>So then I Used Python PIL library to check the pixels of Images
Then I found these Pixels. Intrestingly every Pixel Values Seems to be the ASCII value of alphabets!!!

```
>>> data
[(98, 108, 97), (104, 98, 108), (97, 104, 98), (108, 97, 104), (95, 104, 101), (108, 108, 111), (95, 104, 111), (119, 95, 97), (114, 101, 95), (121, 111, 117), (95, 116, 111), (100, 97, 121), (95, 105, 95), (104, 111, 112), (101, 95, 121), (111, 117, 95), (97, 114, 101), (95, 110, 111), (116, 95, 100), (111, 105, 110), (103, 95, 116), (104, 105, 115), (95, 109, 97), (110, 117, 97), (108, 108, 121), (95, 105, 110), (102, 101, 114), (110, 111, 67), (84, 70, 123), (104, 51, 121), (95, 49, 48), (48, 107, 95), (121, 48, 117), (95, 52, 114), (51, 95, 110), (48, 55, 95), (104, 51, 120), (95, 98, 108), (49, 110, 68), (95, 58, 79), (125, 95, 100), (111, 105, 110), (103, 95, 116), (104, 105, 115), (95, 109, 97), (110, 117, 97), (108, 108, 121), (95, 119, 111), (117, 108, 100), (95, 98, 101), (95, 97, 95), (98, 97, 100), (95, 105, 100), (101, 97, 95), (121, 111, 117), (95, 115, 104), (111, 117, 108), (100, 110, 116), (95, 100, 111), (95, 105, 116), (95, 109, 97), (110, 117, 97), (108, 108, 121), (95, 111, 107)]
>>>

```
<br/>Then Finally written a small exploit to print the FLag.<br/>
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
