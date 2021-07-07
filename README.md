# DDoS Packet Capture Collection

This is a collection of multiple anonymized packet captures of real-world and lab-tested DDoS attacks.

## Goal
The goal of providing these captures is to stimulate the growth of ddos research. 
Real-world DDoS captures are hard to come by which makes research harder.
We are trying to overcome that issue.


## Licence
These captures may be freely used to build and improve DDoS Protection systems. 
Attribution is not required, but greatly appreciated. Do not claim any of these resources as your own.


## Contributing
If these captures or any of our other resources were useful to you, or you just want to help, *Please* contribute through one of our github repositories.

Make sure that these captures only show one-way (incoming) traffic and are atleast 99% real ddos traffic 
(preferably 100%, but this may include things like icmp control messages. Please leave those in.)

If you prefer to anonymize your captures because they may contain real user information. Please do. 
Instructions are below.


## Anonymizing your own packet captures
First, open your capture in wireshark and write a display filter to only select traffic that's part of your attack.
For example `udp && ip.dst == 10.10.10.10 && udp.dstport == 8080`

(optionally) Also anonymize the destination ip. This can for example be done with tcpreplay's tcprewrite
```bash
for file in $(ls);
  do tcprewrite --infile=$file --outfile=/root/anonymous/$file --dstipmap=0.0.0.0/0:10.10.10.10;
done
```
