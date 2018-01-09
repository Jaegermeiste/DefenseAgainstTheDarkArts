[Back to Index](https://jaegermeiste.github.io/DefenseAgainstTheDarkArts/)

## Week 1 Writeup

### Basics of Malware 1 - Wk 1 Lesson 1

The information presented in the early slides is mostly common knowledge, but the presenter significantly expands on the content therein. Watching the videos is essential. Christiaan Beek ([@ChristiaanBeek](https://twitter.com/ChristiaanBeek)) of McAfee obviously knows his stuff.

Later slides provide significantly more new information - for example, I had no prior knowledge of Blackhole or the various RATS, but I was of course aware of Cryptolocker. Regarding the latter ransomware, it was interesting to see how the Bitcoin blockchain was traced back to the original perpetrators. I was particularly impressed to see how trivial it was to extract credit card data form POS machines - a regex makes sense, but I never would have thought that POS machines would maintain a number in memory in plaintext (I would have expected some degree of hashing/salting, like a password). 

Naming conventions are pretty easy to understand, actually. Even the nonstandard ones are clear enough if you are familiar with common abbreviations.

I was aware of VirusTotal [https://www.virustotal.com/](https://www.virustotal.com/), but not malwr [https://malwr.com/](https://malwr.com/) (offline as of this writing) or Comodo's threat analysis tool [https://www.comodo.com/home/internet-security/submit.php](https://www.comodo.com/home/internet-security/submit.php) (I thought they just did SSL certificates).

I was actually aware that .EXE files were PE files, as part of a rabbit hole expedition on Wikipedia about the history of Windows 3.1 and Win32s. A more reliable (and surprisingly human readable) document on PE files is located here: [https://msdn.microsoft.com/en-us/library/ms809762.aspx](https://msdn.microsoft.com/en-us/library/ms809762.aspx).

What is unclear at this point is whether or not I should be trying to log into the VM and do a lab, or if I should drive on with the videos.
