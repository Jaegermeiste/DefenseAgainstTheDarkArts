[Back to Index](https://jaegermeiste.github.io/DefenseAgainstTheDarkArts/)

## Week 2 Writeup

Jason George

### Advanced Forensics 1 - Wk 2 Lesson 3

Recommended Book:
Cliff Stohl - The Cuckoo's Egg: [https://www.amazon.com/Cuckoos-Egg-Tracking-Computer-Espionage/dp/1416507787](https://www.amazon.com/Cuckoos-Egg-Tracking-Computer-Espionage/dp/1416507787)

Forensic Computing - the process of identifying, preserving, analyzing, and presenting digital evidence in a  manner that is legally acceptable. (McKemmish 1999)

Rules for Computer Forensics:
1. Minimize Data Loss
2. Record EVERYTHING
3. Analyze all data collected (evidence)
4. Report Findings

This is interesting and meshes well with much of the training I received in my Master's program - several courses in that program provided the training basis for forensic investigation of crimes and expert witnessing. It also fits well with various Site Exploitation techniques I learned and used in the Army. While those were related to Psychology and hard evidence respectively, the fundamentals are the same.

"Triage" - prove the same conclusion in different ways.

SIEM - Security, Information, and Events Management system (like [http://www.logalyze.com](http://www.logalyze.com))

Locard's Exchange Principle - when two objects come into contact, there will be evidence of the contact.

Like Heisenberg's Uncertainty Principle - you cannot observer and measure the state of the system without changing it.

Order of Volatility:
See RFC 3227 [https://tools.ietf.org/html/rfc3227](https://tools.ietf.org/html/rfc3227)

Proceed from most volatile to last volatile.

FTK Imager looks liek a cool utility, and something I could actually use at work for day-to-day taskjs (unrelated to forensics). 

Volatility [http://www.volatilityfoundation.org/](http://www.volatilityfoundation.org/) is an interesting tool suite.
Yara is an additional plugin for Volatility that can identify malware [https://github.com/VirusTotal/yara/releases](https://github.com/VirusTotal/yara/releases)
Volatility is run using the following syntax: volatility.exe -f <memory_dump_file_name> <plugin_name>
Useful plugins:
-imageinfo
-psscan
-dlllist -p <pid>
-netscan
-deskscan
-getsids

### Advanced Forensics 2 - Wk 2 Lesson 4

I didn't realize that the Windows registry was as volatile as it apparently is.
Reg-Ripper [https://github.com/keydet89/RegRipper2.8](https://github.com/keydet89/RegRipper2.8) essentially dumps the registry with timestamps and access data (per [https://windowsir.blogspot.com/2011/03/using-regripper.html](https://windowsir.blogspot.com/2011/03/using-regripper.html))

Additional useful Volatility plugins:
-timeliner
-MFTparser

MAC time - Modified Accessed Created times

SQLite browser is useful for Firefox and Chrome history and data
DrWatson is also useful

Shellbags - information about Explorer windows

Data Carving - PhotoRec. Essentially lost partition recovery. I have used it at work to (mostly unsuccessfully) recover video and photo data from a dead SD card. Sleuthkit is a super low level tool for to accomplish similar things.

Overall, this week was more tools-focused and practical than last week, which had much more foundation and theory. I feel that there is less to write about the details, but that I am significantly more competent and versed in foresnsics than I was before - that is, I learned something.
