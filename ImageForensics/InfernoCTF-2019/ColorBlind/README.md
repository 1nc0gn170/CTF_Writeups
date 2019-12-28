<h1>Color Blind</h1>

<h4>Exploit.py</h4>

<p>
#!/usr/bin/python3

from PIL import Image

im = Image.open("/home/mindfreaker/Downloads/colorblind.png")
data = list(im.getdata())

for i in data:
	print(chr(i[0]),end="")
	print(chr(i[1]),end="")
	print(chr(i[2]),end="")


</p>

OUTPUT

blahblahblah_hello_how_are_you_today_i_hope_you_are_not_doing_this_manually_infernoCTF{h3y_100k_y0u_4r3_n07_h3x_bl1nD_:O}_doing_this_manually_would_be_a_bad_idea_you_shouldnt_do_it_manually_ok
