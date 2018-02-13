
[Back to Index](https://jaegermeiste.github.io/DefenseAgainstTheDarkArts/)

## Week 5 Writeup

Jason George

### Windows Internals (Kernel Debugging) Lesson 1 - Wk 5

Aditya Kapoor ([linkedin.com/in/kapooraditya](linkedin.com/in/kapooraditya)) is currently Director of Security Architecture at Cyalnce, but was a Research Architect at Intel Security at the time of the video. Cylance [https://www.cylance.com/en_us/home.html](https://www.cylance.com/en_us/home.html) is an AntiVirus vendor with an emphasis on Artifical Intelligence; however, the web site is marketing heavy and information light, so it is unclear what, exactly, the emphasis on AI actually means.

It is a little scary how simple it is (conceptually) to manipulate kernel memory. Signed modules aside, the kernel appears to mimic the flat address space (similar to Windows 3.11 and older/Win16) where the various modules are trusted to be good neighbors and not infringe on one another's memory space (Win32 and later virtualize the address space, at least in user mode). Because of this, any malicious code that manages to execute in kernel space has wide latitude to perform malicious activities. While the power is available, most rootkits use it wisely. A malicious kernel module that simply breaks the system is of little use - it is likely easy to detect and neuter, and will have little value if the system ends up so broken that the user discontinues using it. Better for a rootkit to lie nearly dormant, intercepting and filtering syscalls in as transparent a manner as possible, silently collecting data (and protecting itself) until a chance arises to feed the information back to the hacker's evil lair.

Certain tables make it relatively simple to redirect syscalls, including the SSDT (System Service Descriptor/Dispatch Table) [https://www.adlice.com/kernelmode-rootkits-part-1-ssdt-hooks/](https://www.adlice.com/kernelmode-rootkits-part-1-ssdt-hooks/) and [http://resources.infosecinstitute.com/hooking-system-service-dispatch-table-ssdt/](http://resources.infosecinstitute.com/hooking-system-service-dispatch-table-ssdt/), I/O Request Packets table [https://gerardnico.com/io/request](https://gerardnico.com/io/request), and the Interrupt Descriptor table [https://wiki.osdev.org/Interrupt_Descriptor_Table](https://wiki.osdev.org/Interrupt_Descriptor_Table), and the SYSENTER table [https://wiki.osdev.org/Sysenter](https://wiki.osdev.org/Sysenter). Conversely, sufficiently aware detection software (such as kernel or hypervisor mode antivirus software) can also detect these relatively simple changes and revert them as needed.

Much of the lab work this week involves simply playing with tools we have seen in prior weeks (Cuckoo, WinDbg) as well as some newer, but intuitively familiar tools such as ProcessHacker (similar to ProcessExplorer) and LiveKD (similar to WinDbg).

Usually, there is a practical hurdle that makes executing or following along in the labs for this course more difficult online, and that is the lack of a coherent assignment sheet for the various labs. Usually the objective is clear, but you have to jump all around in the videos to find the salient information in order to accomplish the task. Lab 1 this week is actually an exception to that (a slide exists that outlines exactly what you need to do), but unfortunately the rest don't follow.

### Windows Internals (Kernel Debugging) Lesson 2 - Wk 5

