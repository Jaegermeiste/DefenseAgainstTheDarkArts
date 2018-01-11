[Back to Index](https://jaegermeiste.github.io/DefenseAgainstTheDarkArts/)

## Week 1 Writeup

Jason George

### Basics of Malware 1 - Wk 1 Lesson 1

The information presented in the early slides is mostly common knowledge, but the presenter significantly expands on the content therein. Watching the videos is essential. Christiaan Beek ([@ChristiaanBeek](https://twitter.com/ChristiaanBeek)) of McAfee obviously knows his stuff.

Later slides provide significantly more new information - for example, I had no prior knowledge of Blackhole or the various RATS, but I was of course aware of Cryptolocker. Regarding the latter ransomware, it was interesting to see how the Bitcoin blockchain was traced back to the original perpetrators. I was particularly impressed to see how trivial it was to extract credit card data form POS machines - a regex makes sense, but I never would have thought that POS machines would maintain a number in memory in plaintext (I would have expected some degree of hashing/salting, like a password). 

Naming conventions are pretty easy to understand, actually. Even the nonstandard ones are clear enough if you are familiar with common abbreviations.

I was aware of VirusTotal [https://www.virustotal.com/](https://www.virustotal.com/), but not malwr [https://malwr.com/](https://malwr.com/) (in maintenance mode as of this writing) or Comodo's threat analysis tool [https://www.comodo.com/home/internet-security/submit.php](https://www.comodo.com/home/internet-security/submit.php) (I thought they just did SSL certificates).

I was actually aware that .EXE files were PE files, information discovered as part of a rabbit hole expedition on Wikipedia about the history of Windows 3.1 and Win32s. A significantly more reliable (and surprisingly human readable) document on PE files is located here: [https://msdn.microsoft.com/en-us/library/ms809762.aspx](https://msdn.microsoft.com/en-us/library/ms809762.aspx).

Regarding the VM, in terms of tools, I was familiar with Process Monitor. I've used it to troubleshoot issues with complex vendor software at work. The remainder I was/am unfamiliar with.

What is unclear at this point is whether or not I am supposed to be logging into the VM right now to do the lab, or if I should drive on with the videos.

### Basics of Malware 2 - Wk 1 Lesson 2

The details of Advanced Persistent Threats were interesting - and APT is definitely the sort of acronym that the military uses regularly. 

I am familiar with OSINT from activities in a past life, so none of that was particularly new to me per se, but the specifics of intrusion into computerized systems are largely analagous to those of espionage in general and I found the application of those techniques novel (to me).

The lab walkthroughs were enlightening. Seeing how much information can be gleaned about an execuatble from a few basic tools definitely makes me feel like a tool similar to Dotfuscator [https://marketplace.visualstudio.com/items?itemName=PreEmptiveSolutions.NETObfuscator-Dotfuscator](https://marketplace.visualstudio.com/items?itemName=PreEmptiveSolutions.NETObfuscator-Dotfuscator) should be used for any customer facing production code. I'm looking forward to the lab at this point, but there isn't too much more to note about the lecture (as much of it was hands-on walkthrough).
