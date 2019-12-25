<h1>QueueR</h1><br/>

![Screenshot from 2019-12-25 14-49-36](https://user-images.githubusercontent.com/46676598/71441094-0b4c1f00-2726-11ea-9a46-431bd8ccb00a.png)

Given A packet capture file of an nc connection contains some traffic,PNGs and some Plain texts.Exporting the PNGs reveals that they are QR codes(As the challenge name indicates QueueR).Scanning QR gives some random numbers.After a quick googling reveals that they are actually the names of some books, related to Computer Science.

So then We Tried to connect to the nc connection (`nc 34.89.220.233 6010`).
