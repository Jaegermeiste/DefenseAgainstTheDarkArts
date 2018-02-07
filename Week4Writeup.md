[Back to Index](https://jaegermeiste.github.io/DefenseAgainstTheDarkArts/)

## Week 4 Writeup

Jason George

### Software Vulnerabilities and Common Exploits Lesson 1 - Wk 4

Brad Antoniewicz ([@brad_anton](https://twitter.com/brad_anton)) is currently a Security Research Manager at OpenDNS/Cisco, but was R&D Manager at Intel Foundstone and Adjunct Professor at NYU at the time of the video.

[http://cwe.mitre.org/data/index.html](http://cwe.mitre.org/data/index.html) has various filters and views listing common software vulnerabilities for a programmer to worry about. For example, [http://cwe.mitre.org/data/definitions/14.html](http://cwe.mitre.org/data/definitions/14.html) is an interesting one - compiler optimizations removing code that clears the contents of a buffer (because the buffer is never accessed again afterwards). Thus you need a secure way to zero a buffer wihtout the compiler optimizing it away - either by manually doing something like:

``` C
memset(buffer, 0, sizeof(buffer)); 
buffer[0] = 0;    // Prevent compiiler optimizing away memset by (meaninglessly) accessing it afterward
```

or in Win32, using SecureZeroMemory ([https://msdn.microsoft.com/en-us/library/windows/desktop/aa366877(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/windows/desktop/aa366877(v=vs.85).aspx)) instead of ZeroMemory.

### Software Vulnerabilities and Common Exploits Lesson 2 - Wk 4

Dummy
