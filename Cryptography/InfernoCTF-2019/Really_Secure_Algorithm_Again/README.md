<h1>Really Secure Algorithm Again</h1><br/>

![Screenshot from 2019-12-29 00-09-28](https://user-images.githubusercontent.com/46676598/71548211-15457a80-29d1-11ea-8d49-a6625f518c4f.png)


<br/>
Given a File containing Public Key and Cipher Text

```
e = 65537
N = 25693197123978473
enc_flag = ['0x2135d36aa0c278', '0x3e8f43212dafd7', '0x7a240c1672358', '0x37677cfb281b26', '0x26f90fe5a4bed0', '0xb0e1c482daf4', '0x59c069723a4e4b', '0x8cec977d4159']

Help me find out the secret to decrypt the flag
```
So the first thing I observed is that the Modulus is not soo big number,So I thought it can be factorized into P and Q easily.
Then I used FactorDb to find P and Q values.

`
P = 150758089
Q = 170426657
`
<br/>Voila :).<br/>
Now I can decode the cipher text easily

<h4>Exploit.py</h4>

```
from Crypto.Util.number import *

e = 65537
N = 25693197123978473

P = 150758089
Q = N//P

Phi = (P-1)*(Q-1)

d = inverse(e,Phi)

enc_flag = ['0x2135d36aa0c278', '0x3e8f43212dafd7', '0x7a240c1672358', '0x37677cfb281b26', '0x26f90fe5a4bed0', '0xb0e1c482daf4', '0x59c069723a4e4b', '0x8cec977d4159']

plaintext = ""

for i in enc_flag:
	i= int(i,16)
	plaintext+=long_to_bytes(pow(i,d,N)).decode()

print (plaintext)

```

FLAG : `infernoCTF{RSA_k3yS_t00_SmAll}`
