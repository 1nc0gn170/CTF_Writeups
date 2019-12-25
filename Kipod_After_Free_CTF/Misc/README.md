<h1>QueueR</h1><br/>

![Screenshot from 2019-12-25 14-49-36](https://user-images.githubusercontent.com/46676598/71441094-0b4c1f00-2726-11ea-9a46-431bd8ccb00a.png)

Given A packet capture file of an nc connection contains some traffic,PNGs and some Plain texts.Exporting the PNGs reveals that they are QR codes(As the challenge name indicates QueueR).Scanning QR gives some random numbers.After a quick googling reveals that they are actually the names of some books, related to Computer Science.

So then We Tried to connect to the nc connection (`nc 34.89.220.233 6010`).

![Screenshot from 2019-12-25 15-18-11](https://user-images.githubusercontent.com/46676598/71441997-f5d8f400-2729-11ea-99d3-31ac67659ab5.png)

So it gives the raw data of an Image.

<h4>Steps to Solve:</h4>
<ul>
  <li>Create an Image with the given raw data.</li>
  <li>Scan the QR inside the Image and Fetch the Book Number</li>
  <li>Using Book number,Fetch the book name and Send it back to the server</li>
</ul>

So,We need to Automate this process for  30 Iterations, finally after all iterations flag will be displayed.:)
You Can See my Automation Script(`Exploit.py`).
  
```(9780133594140, 26)
Computer Networking: A Top-Down Approach (7th Edition)
(9780201633610, 27)
Design Patterns: Elements of Reusable Object-Oriented Software
(9781118825099, 28)
The Art of Memory Forensics: Detecting Malware and Threats in Windows, Linux, and Mac Memory
(9781593278267, 29)
Serious Cryptography: A Practical Introduction to Modern Encryption
[*] Switching to interactive mode
KAF{k4r1_m4rx_15_7h3_b357}[*] Got EOF while reading in interactive
$  ```

<b>`Flag: KAF{k4r1_m4rx_15_7h3_b357}`</b>
