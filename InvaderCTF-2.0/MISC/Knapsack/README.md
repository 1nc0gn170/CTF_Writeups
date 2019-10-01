
## 1. Knapsack (498)

<b>Description : Walk Through the tunnel of Knapsack<br/>Connection : nc 10.11.4.98 13377</b>

Given a netcat connection and that basically runs on super increasing knapsack.

For More Information about Super increasing Knapsack refer this link<br>
<a href="https://en.wikipedia.org/wiki/Merkle%E2%80%93Hellman_knapsack_cryptosystem">SuperIncreasing Knapsack</a>



#Exploit.py

```
#!/usr/bin/python

'''
	Author : Naina

'''

from pwn import *


def solve(elements_list,calc_sum):
	calc_elements = []

	for i in sorted(elements_list)[::-1]:
		if (i<=calc_sum):
			if (calc_sum-i<0):
				continue
			else:

				calc_elements.append(i)
				calc_sum-=i
		else:
			continue
	result = [calc_elements if (calc_sum==0) else ["Error:"]]

	return sorted(result[0])


if __name__ == '__main__':

	sh = remote("10.11.4.98",13377)

	for i in range(256):
		print (i)
		sh.recvuntil("Knapsack:")
		data = (sh.recvrepeat(0.001)[2:-1]).split('\n')

		payload = map(int ,data[0][1:-2].replace("L","").split(', '))
		cal_sum = int(data[2].split(': ')[1])
		solved = str(solve(payload,cal_sum)).replace("L","")[1:-1]

		sh.sendline(solved)
	sh.interactive()
	sh.close()

```
So My exploit will be able to solve the whole Knapsack within 15 secs ;).


```
[*] Switching to interactive mode
Nice Try :)Invader{S1mpl3_Sup3r_1ncr34s1ng_kn4p54ck}
[*] Got EOF while reading in interactive
$  
```

Flag: 'Invader{S1mpl3_Sup3r_1ncr34s1ng_kn4p54ck}' 


