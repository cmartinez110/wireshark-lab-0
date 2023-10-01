<h1>Introduction to Wireshark Lab</h1>


<h2>Description</h2>
In this project, I analyzed traffic and answered basic questions (destination, header, ttl). As I become proficient in packet capture and network traffic analysis, I will post better projects!
<br />

<h2>Languages and Utilities Used</h2>

- <b>Wireshark</b> 

<h2>Environments Used </h2>

- <b>Windows 11</b>

<h2>Project walk-through:</h2>

<p align="center">
After opening the virtual machine, I opened the pcap file to execute Wireshark: <br/>
<img src="https://i.imgur.com/otzmy5x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next I filtered by "ip.addr == 142.250.1.139". This narrowed down the search criteria to destination or source IP addresses that natch my filter. There are only two types of packets. ICMP and TCP (also HTTP which is a subset of TCP):  <br/>
<img src="https://i.imgur.com/WYdtFEH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The frame sub-tree was selected: <br/>
<img src="https://i.imgur.com/ji6rqSh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next Ethernet II sub-tree was selected:  <br/>
<img src="https://i.imgur.com/sCpp9bO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Then Internet Protocol Version 4 (ipv4) is selected. We are just perusing the different sub-trees:  <br/>
<img src="https://i.imgur.com/BUMlYoh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now Transmission Control Protocol sub-tree is selected (TCP). I was able to determine that the destination port is port 80:  <br/>
<img src="https://i.imgur.com/3uKu5RX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Here in the flag sub-tree we can see more data about the flags of the packet:  <br/>
<img src="https://i.imgur.com/mLW44A2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I closed out of that window and searched for criteria based on "ip.src == 142.250.1.139" (source IP) :  <br/>
<img src="https://i.imgur.com/WeocBQD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The same search is done for ip destination (ip.dst == 142.250.1.139):  <br/>
<img src="https://i.imgur.com/LkWiUJx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Results are filtered by MAC address using "eth.addr == 42:01:ac:15:e0:02". Was abke to navigate to the ipv4 sub-tree and locate the protocol for the first packet related to the MAC address:  <br/>
<img src="https://i.imgur.com/O11510p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
"udp.port == 53" is applied as a filter:  <br/>
<img src="https://i.imgur.com/QcRkdh7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Was able to find a specific IP address in the sub-trees:  <br/>
<img src="https://i.imgur.com/5KmByg2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Finally, I filtered with "tcp.port == 80". Was able to find the time to live of a packet. I also located the frame length in the  frame sub-tree. As a conclusion to this lab, I answered  questions abotut the length of the header and the destination IP, in the ipv4 sub-tree:  <br/>
<img src="https://i.imgur.com/ciIvebu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
