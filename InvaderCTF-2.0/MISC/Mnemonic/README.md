
## Mnemonic

`Description: I'm suffering from amnesia.<br/>Could you please help me.` <br/>
<b>`Connection: `</b>` nc 10.11.4.98 13378 `

Connecting to the netcat will ask you to guess something and if u fail to guess that correctly, then it will return the correct answer and exit.

So if u observe the pattern of correct answers, it is same everytime (I mean the connection is generating a specific pattern of correct answers.

So u need to store them in a list and u need to feed those to the server.
# Exploit.py
```
#!/usr/bin/python

from pwn import *


def main():

	stored=[]
	data = ""
	while(1):

		print(len(stored))

		sh =remote("10.11.4.98",13378) 

		for i in stored:
			sh.recvuntil(")>")

			sh.sendline(i)
			data=sh.recvrepeat(0.001)

	

		if "Invader" in data:
			print (data)
			sh.interactive()
			break

		sh.recvuntil(")>")
		sh.sendline("laksdjflaksdjf")
		data=sh.recv()

		stored.append(data.split(":")[1][1:-2])



if __name__ == '__main__':
	main()
```

After 100 iterations you'll get the flag :) 

Flag : 'Invader{y0u_4r3_Au70m5t3d_mn3m0n1c!!!}'
