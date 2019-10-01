<h1>SunshineCTF</h1>
<ul>
  <li><h3>Golly Gee Willikers</h3></li>
  <li><h3>Sonar</h3></li>

</ul>
<br/>

<h1>Golly Gee Willikers (100)</h1><br/>
<h4><u><b>Description:</b></u></h4><br/><br></h5>Someone sent me this weird file and I don't understand it. It's freaking me out, this isn't a game! Please help me figure out what's in this file.</h5><br/>

We've given a file `golly_gee_willikers.txt`.
After a quick search of contents in the given file,I got to know it is a `rle file (rule)` used by ``Conway's Game of Life``,What actually it does is,It will print the patterns.<br/>
<br/>So I searched for a simulator for the pattern generator,I found `golly`.It is a pretty good tool for Linux and it is so handy to use.Otherwise you can also try to simulate online<br>
When I open the pattern file in I got Alphanumeric which doesn't make any sense.<br/>
<br/>![First](https://user-images.githubusercontent.com/46676598/55304429-098c4e00-5469-11e9-9453-d144ac207030.png)<br/>

Finally read the documentation of .rle file,There I've got to know that about the symbols and their purpose.
<ul>
  <li>`x` Represents `Width`</li>
  <li>`y` Represents `height`</li>
  <li>`o` Represents the `off cells`</li>
  <li>`b` Represents `on cells`</li>
  <li>`$` Represents `End of line`</li>
  <li>`!` Represents `End Of Pattern`</li>
</ul>

`!` Plays a major role in this challenge,If u can observe carefully you could file two `!` symbols,that means two patterns.Then I quickly removed the first pattern and then loaded into `golly`.Got The Flag :)<br/>
<br/>![Final](https://user-images.githubusercontent.com/46676598/55304728-91268c80-546a-11e9-91bd-8fefdcc6a544.png)
<br/>
`Flag : sun{th1s_w0nt_last}`



<br/><h1>Sonar (250)</h1><br/>
<br><h3>Description</h3>
<h4>We think a wrestler called Sonar wants to re brand and go to a competitor. We have to reason to believe that he was sending them his new wrestling name, lucky that our next-gen firewall was capturing the traffic during the time where he sent that info out. Unfortunately our staff cannot make heads or tails of it. Mind looking at it for us?</h4><br/>

![first](https://user-images.githubusercontent.com/46676598/55317339-ef189b80-548d-11e9-90b3-f3e6c78fb653.png)
We've given a packet capture file(pcapng file).After wasting 2 hrs of time i got concentrated on ICMP packets(Found Suspicious because ping requests are in between other packets and it has data),then tried to analyse the ICMP data then finally as a guess tried to change the data bytes to its character value (i.e, `chr(115)='s'`,`chr(117)='u'`,`chr(110)='n'`....) So on continue to decode and get the flag :)
![final](https://user-images.githubusercontent.com/46676598/55317338-ee800500-548d-11e9-94b2-232218327151.png)

Finally got the flag :)

Flag: `sun{7UcHa_L1Br3}`
