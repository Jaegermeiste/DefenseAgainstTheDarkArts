[Back to Index](https://jaegermeiste.github.io/DefenseAgainstTheDarkArts/)

## Week 3 Writeup

Jason George

### Malware Defenses Lesson 1 - Wk 3

Craig Schmugar [@craigschmugar](https://twitter.com/craigschmugar) is currently a Principal Engineer at McAfee, and has been employed there in one capacity or another since 2000.

The phases of the malware infection/exploitation attack graph are useful because it enables both a conversation targeting specific portions of the attack, but also because it conceptually lends itself to defense in depth. Naturally there are a myriad of attack vectors, almost all of which exploit people's trust or ignorance in order to obtain credentials or remotely execute code on a target system in order to establish a beachhead. The beachhead is what was explored in some depth during the last Lab. That is follwed by various malicious actvities, which (obejctively) are some of the least interesting parts - because at this point (generally), the malicious actors' objective has been obtained.

More of a deeper dive into Yara [https://github.com/VirusTotal/yara/releases](https://github.com/VirusTotal/yara/releases) plugins this week - the string pattern matching is an interesting strategy to identify related malware (or related programs, period). Leveraging FileInsight to obtain an intial set of strings to exploit (based on a known piece of malware) makes a lot of sense, especially given the common inheritance of many malware kits.

### Malware Defenses Lesson 2 - Wk 3

It is interesting to see that unique malware formas are growing exponentially - my instanct would have been that unique forms would actually decrease somewhat, given the prevalance of script kiddies and premade malware toolkits for sale on the dark web. I suppose that is partially dependent on the semantic definition of unique, though.

Cuckoo Sandbox[https://www.cuckoosandbox.org/](https://www.cuckoosandbox.org/) is an interesting tool, but it seems like it may duplicate a lot of functionality found in the other analysis tools.

Based on the samples in MalwareDefense:
Your name
Date/Time of your “posting” (completion)
Malware hash
Yara signature
Your analysis
