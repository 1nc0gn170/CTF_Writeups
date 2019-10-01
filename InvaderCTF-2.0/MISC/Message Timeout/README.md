
## 1. Message Timeout (1000)

`Description :I sniffed my friends secret message.` <br/>
`Can you figure it out?`

So actually title of the challenge speaks everything :).

You need to figure out messaging protocol in pcap.The only messaging protocol in the capture is `ICMP (Internet Control Message Protocol)` 

If u can observe there is a field called `time to live (Which is timeout or ttl)` which holds the real secret message.

![Screenshot from 2019-09-29 19-55-27](https://user-images.githubusercontent.com/46676598/65854788-1ab40a00-e37b-11e9-8c93-1b598327131a.png)


So u need to extract those bits inorder to get the secret.I've used tshark to do that

```tshark -r capture.pcap -T fields -Y "icmp && ip.src==192.168.43.26" -e ip.ttl > data```

-r reads pcap<br/>
-Y used to filter<br/>
-e used to extract<br/>

So we have bits now, joining altogether gives the secret.

```
>>> ''.join([chr(int(i)) for i in open('data').read().split('\n')[:-1]])
'Password:1cmp_sn1ff_m4st3r'
>>> 
```

Password? What to do with that?
If u run binwalk,you can see a zip embedded into the pcap.

`
Zip archive data, encrypted at least v2.0 to extract, compressed size: 329779, uncompressed size: 332155, name: 1nv4d3r/intresting.png
`
![Screenshot from 2019-09-29 19-59-51](https://user-images.githubusercontent.com/46676598/65855202-39ff6700-e37c-11e9-9481-8a3e922e7b43.png)

So extract that using the password.Yeah there is an image (intresting.png), and it displays 
`Great Hacker! Btw Thanks for playing`.

No flag :( . So if u see the image clearly the text inside the image seems slightly moved towards bottom (Not Extactly placed).

So actually flag is placed at the bottom of the image,I've changed the image length bit.

````
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4948 4452  .PNG........IHDR
00000010: 0000 03e8 0000 024a 0806 0000 00bf 006f  .......J.......o
00000020: b500 0020 0049 4441 5478 9cec bdcb 96e4  ... .IDATx......
00000030: 48ce a017 e177 77de 3c32 abff eaee 0abf  H....ww.<2......
00000040: 7b64 56f7 fff7 fc57 1d9d 998d 1692 763a  {dV....W......v:
00000050: 33b3 d55e 4fa2 a397 d052 7a09 3d9e 6941  3..^O....Rz.=.iA
00000060: c208 8301 0618 498f 88ac ae05 8e67 86d3  ......I......g..
00000070: 49a3 5df1 0130 d8d3 6afd 27b7 5aff c92d  I.]..0..j.'.Z..-
00000080: 37ad ccb7 adcc 3a99 9707 372f 0f6e 51f0  7.....:...7/.nQ.
00000090: b2dc 2952 1e03 5954 adcc eaf6 7359 be7a  ..)R..YT....sY.z
````

24th bit(4a) indicates the length of image,increasing the value will give the flag.

After changing that u need to correct CRC of image.

![Screenshot from 2019-09-29 20-01-59](https://user-images.githubusercontent.com/46676598/65855192-3370ef80-e37c-11e9-90c3-3da1884c1cc5.png)




```
$ pngcheck intresting.png 
intresting.png  CRC error in chunk IHDR (computed aee87101, expected bf006fb5)
ERROR: intresting.png
```

Correcting CRC will give u flag. :)

![Screenshot from 2019-09-29 20-02-12](https://user-images.githubusercontent.com/46676598/65855180-2c49e180-e37c-11e9-9fdc-1f91c36bd872.png)

Flag: 'Invader{y0u_g0t_dud3_w3ll_played}' 


