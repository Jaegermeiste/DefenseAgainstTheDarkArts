[Back to Index](https://jaegermeiste.github.io/DefenseAgainstTheDarkArts/)

## Week 6 Writeup

Jason George

### Network Security Lesson 1 - Wk 6

Ram Venugopalan ([https://securingtomorrow.mcafee.com/author/ramnath-venugopalan/](https://securingtomorrow.mcafee.com/author/ramnath-venugopalan/)) is currently a principal architect at McAfee. Geoffery Cooper ([https://www.linkedin.com/in/geoffrey-cooper-8b28a8/](https://www.linkedin.com/in/geoffrey-cooper-8b28a8/)) is currently a Principal Engineer of IoT Security Solutions at Intel.

#### Firewall HW
<img src="WK6_Firewall_HW.PNG" alt="">

Many of the concepts here are familiar to me. I have a CCNA in Routing and Switching, and access control lists and defense in depth are very basic concepts anyway. The firewall homework above was pretty vague in requirments, very high level, but I guess the intent is jsut to get students thinking along those lines without the actual muck of an ACL.

The Lab 2 assignment is submitted separately via Canvas. What a massive pain - I had to manually maintain and synchronize roughly 300 lines of code on both my computer and the VM. Simply because of the administrative headache, that might be the worst Lab I have done in any course in the program. There doesn't seem to be a good reason that the CSV files have to live on the VM - they aren't viruses - but I suppose that's where they ended up initially (at course creation) and there they stayed.

Honeypots/Honeynets - an interesting idea. I have seen a lot of home builds based on Raspberry Pi, but I never really saw the need beyond academic curiosity. It is interesting to see how they might be deployed on a larger scale. The linked Nova episode on this topic is mildly terrifying for all sorts of reasons:

<iframe width="560" height="315" src="https://www.youtube.com/embed/EcKxaq1FTac" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

The SSL/TLS discussion is interesting, especially how it relates to Man in the MIddle attacks.

#### Robustness HW
<img src="WK6_Robustness_HW.PNG" alt="">

1. I would suggest being conservative in what you accept, rejecting the rest, and also being conservative in what you send.
2. It is definitely best to assume that pretty much everything is trying to break your system.
3. Human malice has certainly gone farther than disrupting networks.
4. Token ring vampire taps and NetBIOS, anyone? I'd rather some TCP/IP over 40 GbE...
5. This is just good programming practice.
6. This is also just good programming practice.
7. This is interesting in the context of rootkits and antivirus software, but in general, your application should not mess with the undocumented API (or the deprecated/obscure stuff that nobody uses).
8. This is similar to the FCC requirement that electronics must happily accept interference while also not generating any. Makes sense in both contexts.

### Network Security Lesson 2 - Wk 6

Nmap (actually the Windows GUI variant zenmap) is a tool I use often at work, because I don't trust Solarwinds or ping to tell me that an IP address is clear for use. I have also used Wireshark extensively in the past for work, CCNA, and the Netowrking class in this program. 

Many of the threats here  - spoofing, DoS/DDoS, et cetera, are not new to me. I was extremely interested in the discussion regarding NAT. I have always felt that NAT provides security though obscurity - a major disadvantage of un-NATed IPv6 is that anybody can see into your glass house and know all the names of the machines and get some sense of how they're connected. I'm I'm running a 10.x.x.x network behind a NAT at some random IP address, you don't know much about my organization other than the external IP. It was interesting to see some of the ways to elicit information about what is behind a NAT (from the outside).

The idea of deploying IPSec universally across networks is an interesting one, and one that I think is a good idea; however, for it to be practical I think consumer network hardware will need ASICs for IPSec - relying on the CPU will be too slow on the scale of the Internet.

I have always wanted to play with an Intrusion Proteciton System. It is out of my reach where I'm at in the Cisco world - I have an ASA 5505, but that's basically a firewall.

The software definied networking information left me wanting more - I wish some more time had been spent on it and how it might be vulnerable.
