# InvaderCTF

# Forensics Writeup:

  Here Are The Writeups Of Five Forensics Challenges From InvaderCTF

# 1. Easy Peasy (150)
## Don't Mess The Things Up...!

In This Challenge You'll Find A QR Code.Scan QR Code.

After Scanning The QR Code We'll Get: "w3lc0m3_70_1nVd3r_CtFstrings challenge.png"

![screenshot from 2019-01-14 18-06-52](https://user-images.githubusercontent.com/46676598/51113676-d0a8e980-1828-11e9-8005-931a40a131a9.png)

But Actually Here There Is A Main Hint "Strings".Strings Is a Linux Command Which will Give Us All Readable Strings In That Image

![screenshot from 2019-01-14 18-07-19](https://user-images.githubusercontent.com/46676598/51114044-1fa34e80-182a-11e9-867a-a75b6019d9e7.png)

Something Is Weird Right...!
Actually It Is Base32 Encoding,So Simply Decoding It Gives You The Flag

![screenshot from 2019-01-14 18-08-03](https://user-images.githubusercontent.com/46676598/51114062-2cc03d80-182a-11e9-8637-ea1931525d99.png)

Flag: 'invader{345y_P34sY_l3m0n_Squ33zy!!}' 



# Dirty Room (100)

In This Challenge Linux Users Will Face Extraction Problem, Actually It Was An Intended One, I Changed Magical Numbers Of Zip File.

![screenshot from 2019-01-14 18-36-09](https://user-images.githubusercontent.com/46676598/51114909-b2dd8380-182c-11e9-9874-b3cbbb217db5.png)

So, Inorder to Extract It You've To Change "11 91" with "50 4B" (Magical Numbers Of Zip File: 50 4B 03 04),SO after Changing Magical Numbers You Can Extract The Zip. 

After Unzipping you'll Find Some Random Images, Among Those U Can See A Password. Now We've The Password,But What To Do With That.

![screenshot from 2019-01-14 18-38-22](https://user-images.githubusercontent.com/46676598/51114919-bb35be80-182c-11e9-9b81-9c6741dbe6aa.png)

If U Can Observe Clearly There Is An Image('maxeresdefault(1).jpeg') Which Doesn't Showup. Using Linux Command "File" We Can Find The Type Of File 
![screenshot from 2019-01-14 18-44-05](https://user-images.githubusercontent.com/46676598/51114933-c688ea00-182c-11e9-85f7-e258bc4cda74.png)

Woww...! It's A Zip File.Change Image Extension "jpeg" To "zip".


![screenshot from 2019-01-14 18-44-12](https://user-images.githubusercontent.com/46676598/51114941-cd176180-182c-11e9-9527-7ba2226566cc.png)

Now Try to Unzip The File. It'll Prompt For Password.Hey...! We've A Password Right? Enter The Password, You'll Get The Flag :)

![screenshot from 2019-01-14 18-45-00](https://user-images.githubusercontent.com/46676598/51114952-d4d70600-182c-11e9-838d-2070748181bc.png)

Flag : 'invader{1_l0v3_f1l3_f0r3n51c5}'



# Dig Deeper (300)

In This Challenge You'll Have An Image With A Hint 

# Hint 

we use "nopassword" to dig more...............

Now We've A Password "nopassword", And We've An Image.

So Try Steganography(It Is An Art Of Hiding Data)

We've Many Online Tools For Steganography. But I've Steghide.

So Trying Steghide Will Give U A File Named "Flag.txt". But Inside You'll Find "You can't find flag here.Better dig once again"
Sorry Just For Fun :) 

![screenshot from 2019-01-14 19-11-05](https://user-images.githubusercontent.com/46676598/51116548-73656600-1831-11e9-8362-9d36d39bba9c.png)

So There Trying Strings, And Other Commands Will Leave U No Clue.So There Is Nothing Inside 

![screenshot from 2019-01-14 19-13-24](https://user-images.githubusercontent.com/46676598/51116550-73fdfc80-1831-11e9-9fce-94783421db02.png)

Try to Analyse The Given Zip File. Using Binwalk(Linux Command To Show Embedded Files In A File) You'll Find An Image.
(Command: binwalk Challenge3.zip)

Now Try To Extract Image (Command: binwalk --dd='.*' Challenge3.zip).

Now Try Steganography On This Image With Given Password.

You'll Get Flag.txt, containing "Yeah Man...! You nailed it
You Deserve The Flag.
Here You Are
Link:https://drive.google.com/open?id=12OMTbBiJ0oXsukdcnypE_S3mlqBgN9NU"

![screenshot from 2019-01-14 19-14-41](https://user-images.githubusercontent.com/46676598/51116556-76f8ed00-1831-11e9-8346-5848e60024b7.png)

Using Link We'll Get Flag

Flag : invader{W3LCoM3_70_F0r3N51C5}



# Long Walk To Freedom

We've An Audio File & Image

Search For Audio Forensics.You'll Find Many Tools & Now I'll be using Audacity.

Open Audio File With Audacity.You'll get Waveform Of Audio


![screenshot from 2019-01-14 19-47-58](https://user-images.githubusercontent.com/46676598/51118752-1ff61680-1837-11e9-8878-5aa80b9a282d.png)

Change It To Spectrogram.

![screenshot from 2019-01-14 19-48-17](https://user-images.githubusercontent.com/46676598/51118754-208ead00-1837-11e9-894f-e11535261b0c.png)

"5h1zuk4_143" (Shizuka_143)...A Password It Seems.We've An Image Too.Soo Try Steganograpy

![screenshot from 2019-01-14 19-51-51](https://user-images.githubusercontent.com/46676598/51120364-ecb58680-183a-11e9-88e3-d42324c16751.png)

Wow ....! It Returned Redirect.txt & We've A Mediafire Link,It Gives Us "Nobitha.mp3"

Listen To It Once,This Sound Indicates Morse Code In It.

We've A Online Decoder : 'https://morsecode.scphillips.com/labs/audio-decoder-adaptive/'

Upload Audio & Play.

![screenshot from 2019-01-14 19-55-10](https://user-images.githubusercontent.com/46676598/51118756-21274380-1837-11e9-9486-ccdab4ff11e5.png)

Decoded Text Is Full Of 'A' & 'B'. Search For Ciphers With 'A' & 'B'.

"Baconian Cipher"

Exclude "QWZXWEDC" And Decode It. Link: "http://rumkin.com/tools/cipher/baconian.php"

![screenshot from 2019-01-14 19-56-11](https://user-images.githubusercontent.com/46676598/51118757-21bfda00-1837-11e9-916d-6a05f23d0a93.png)

Flag : invader{YOUHAVEGREATPATIENCE}

# Brain WhiteWash (550)

Really Cool Challenge :)

We are Provided With A Zip File & Hint

# Hint :

This Time A Little Bit Crypto :)
Cipher Text: kyreb5wfiaf1exfli7urpvmvek4euefntfdzexk0tyrcc3exvefvhlrcjpdsfcjaljkgrjjnfiuzjtrktyd331wlt4ee==

It Is "Caeser Cipher With Shift 17" & Zip Password : "catchm331fuc4nn"

![screenshot from 2019-01-14 21-45-50](https://user-images.githubusercontent.com/46676598/51125635-1379ba00-1847-11e9-9604-f27691bf1896.png)
Extract The Zip With Decoded Password.
Inside You'll Find Three Files "Chal.png" Which Is Useless(Use Strings & you Can Find Waste Many A Times) , "MainHint.txt" Which Is Full Of Binaries & Finally "No Security In This World".

Consider "MainHint.txt".Use LSB(Least Significant Bits Of Each Binary) And Decode It.

![screenshot from 2019-01-14 21-53-56](https://user-images.githubusercontent.com/46676598/51125650-15dc1400-1847-11e9-85de-aed2336f946b.png)

Code For Decoding 

![screenshot from 2019-01-14 21-50-09](https://user-images.githubusercontent.com/46676598/51125636-14125080-1847-11e9-8c1b-aab6d1390c79.png)

Woww...! "snowstegisawesome".

I Guess It Is Related To Snow Steganography.

Then What About The Other File...?

Run Binwalk. You'll Find A JPEG File
Extract It.
![screenshot from 2019-01-14 21-50-53](https://user-images.githubusercontent.com/46676598/51125639-14125080-1847-11e9-95e0-a2cdb30930f8.png)

But This Time We Only Have Image Bt No Password..... :(

![screenshot from 2019-01-14 21-51-59](https://user-images.githubusercontent.com/46676598/51125641-14125080-1847-11e9-8699-415955c33c84.png)

Wait..! What Was The File Name "No Security In This World". I Guess There Is no Password.

Yeah Extracted Hint File.
![screenshot from 2019-01-14 21-52-24](https://user-images.githubusercontent.com/46676598/51125644-14aae700-1847-11e9-87a7-cd4c85cb1e96.png)
In The Begining I Thought It Was Empty.
![screenshot from 2019-01-14 21-52-43](https://user-images.githubusercontent.com/46676598/51125645-14aae700-1847-11e9-9c25-9b0cb04a9d31.png)
But In The End We've A Clue.Which Won't Help Us.

Hold on...! Challenge Name "Brain WhiteWash" Right....

Yeah If u Have Really Enquired Abt Stegsnow,You Could Easily Find It Out What It Is.It Is White Space Steganography

See This Is White Space Stego.Really The Best Stego Ever.

![screenshot from 2019-01-14 21-52-52](https://user-images.githubusercontent.com/46676598/51125646-15437d80-1847-11e9-9410-3b10a3a96180.png)


Using Snow Steg & Password We can Retreive The Flag.

![screenshot from 2019-01-14 21-53-32](https://user-images.githubusercontent.com/46676598/51125648-15437d80-1847-11e9-9623-b6be3f8c22de.png)


Flag: 'invader{W0W_Y0u_h4v3_gr34t_futur3}'



