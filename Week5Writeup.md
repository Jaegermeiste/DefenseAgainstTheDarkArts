
[Back to Index](https://jaegermeiste.github.io/DefenseAgainstTheDarkArts/)

## Week 5 Writeup

Jason George

### Windows Internals (Kernel Debugging) Lesson 1 - Wk 5

Aditya Kapoor ([linkedin.com/in/kapooraditya](linkedin.com/in/kapooraditya)) is currently Director of Security Architecture at Cylance, but was a Research Architect at Intel Security at the time of the video. Cylance [https://www.cylance.com/en_us/home.html](https://www.cylance.com/en_us/home.html) is an AntiVirus vendor with an emphasis on Artifical Intelligence; however, the web site is marketing heavy and information light, so it is unclear what, exactly, the emphasis on AI actually means.

It is a little scary how simple it is (conceptually) to manipulate kernel memory. Signed modules aside, the kernel appears to mimic the flat address space (similar to Windows 3.11 and older/Win16) where the various modules are trusted to be good neighbors and not infringe on one another's memory space (Win32 and later virtualize the address space, at least in user mode). Because of this, any malicious code that manages to execute in kernel space has wide latitude to perform malicious activities. While the power is available, most rootkits use it wisely. A malicious kernel module that simply breaks the system is of little use - it is likely easy to detect and neuter, and will have little value if the system ends up so broken that the user discontinues using it. Better for a rootkit to lie nearly dormant, intercepting and filtering syscalls in as transparent a manner as possible, silently collecting data (and protecting itself) until a chance arises to feed the information back to the hacker's evil lair.

Certain tables make it relatively simple to redirect syscalls, including the SSDT (System Service Descriptor/Dispatch Table) [https://www.adlice.com/kernelmode-rootkits-part-1-ssdt-hooks/](https://www.adlice.com/kernelmode-rootkits-part-1-ssdt-hooks/) and [http://resources.infosecinstitute.com/hooking-system-service-dispatch-table-ssdt/](http://resources.infosecinstitute.com/hooking-system-service-dispatch-table-ssdt/), I/O Request Packets table [https://gerardnico.com/io/request](https://gerardnico.com/io/request), and the Interrupt Descriptor table [https://wiki.osdev.org/Interrupt_Descriptor_Table](https://wiki.osdev.org/Interrupt_Descriptor_Table), and the SYSENTER table [https://wiki.osdev.org/Sysenter](https://wiki.osdev.org/Sysenter). These tables seem to be analogous to C++ vtables, in that they are simply compact lists of pointers that can be overidden (usually deliberately in C++). Conversely, sufficiently aware detection software (such as kernel or hypervisor mode antivirus software) can also detect these relatively simple changes and revert them as needed.

Much of the lab work this week involves simply playing with tools we have seen in prior weeks (Cuckoo, WinDbg) as well as some newer, but intuitively familiar tools such as ProcessHacker (similar to ProcessExplorer) and LiveKD (similar to WinDbg). Tuluka is a very powerful tool that displays the system tables and highlights suspected malicious changes in them.

Usually, there is a practical hurdle that makes executing or following along in the labs for this course more difficult online, and that is the lack of a coherent assignment sheet for the various labs. Usually the objective is clear, but you have to jump all around in the videos to find the salient information in order to accomplish the task. This week is actually a refreshing exception to that (for most of the labs, a slide exists that outlines exactly what you need to do).

#### Agony

Create debug break points (in debugger VM) using bp instruction on the addresses hooked by wininit for the three hooked APIs.

When the debugger breaks , use f8 to step through one instruction at a time.
Find the offset of the instruction from the beginning of the function boundary. Report the offset.
0. NtEnumerateValueKey: Breakpoint 9b140480 hit at wininit+0x1480, and returned to nt!NtEnumerateValueKey at wininit+0x14d4. 0x14d4-0x1480 = 0x54 = 84 bytes decimal.
1. NtQueryDirectoryFile: Breakpoint 9b140050 hit at wininit+0x1050, and returned to nt!NtQueryDirectoryFile at wininit+0x1086. 0x1086-0x1050 = 0x36 = 54 bytes decimal.
2. NtQuerySystemInformation: Breakpoint 9b13ff00 hit at wininit+0xf00, and returned to nt!NtQuerySystemInformation at wininit+0xf1a. 0xf1a-0xf00 = 0x1a = 26 bytes decimal.

### Windows Internals (Kernel Debugging) Lesson 2 - Wk 5

Day 2 covers stealth techniques other than rootkits, such as bootkits. Essentially, these modify the Master Boot Record to load the bootkit instead of the NT kernel, installing a rootkit then loading into privleged memory and then loading Windows as usual. So the bootkit hijacks the boot process, and uses the privledges gained to install the rootkit, which then actively hides both components form the operating system (and subsequently, anti virus applications).

This forging process, where malware essentially caches a copy of the unmodified MBR or system file somewhere and returns it when queried (essentially masking the interception/modification) is common to most rootkits, and can be used to mask changes to disk and memory.

Watcher threads can counter antivirus repaitrs to remove hooks, as well as actively attack AV processes. The Brazilian Banker rootkit interestingly made use of the PsSetLoadImageNotifyRoutine callback in order to preemptively corrupt processes that it didn't want running (like AntiVirus). 
