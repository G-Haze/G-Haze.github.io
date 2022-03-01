## IoC Skills Bootcamp Week 4 - Metasploit

This week we looked at another very commonly used offensive security testing tool, the Metasploit Framework, that can be used to probe vulnerabilities on networks and servers and deploy known attack vectors (CVEs) against them. As usual, to aid with our learning we would be completing the [Metasploit](https://tryhackme.com/room/rpmetasploit) room on tryhackme.

Metasploit consists of six core modules that make up the majority of the tools available; Auxilliary, Exploit, Post, Encoders, Payload, and NOP. These modules can be associated with the various stages of the Lockheed Martin Cyber Kill Chain. They cover an extremely broad range of functions against many systems ranging from Linux and Windows enumeration to modules that act as an [Amazon Fire TV Remote Control](https://www.infosecmatter.com/metasploit-module-library/?mm=auxiliary/admin/firetv/firetv_youtube).

We can begin gathering information on the target machine by using `db_nmap`. This works the same as nmap but will store the results into the postgresql database which can be referred back to when required. It is also possible to import any port or vulnerability scan results into the database by using `db_import`. To perform further reconnaissance we could choose use of one the many auxiliary modules packaged with Metasploit for scanning, fuzzing or sniffing if suitable. Auxiliary modules are not exploits but...

After gathering sufficient information to identify a weakness, we can search through Metasploit's vast and extensible database for an appropriate exploit. Exploits within Metasploit are given rankings ranging from Low to Excellent based on how reliable they are and whether they are likely to crash the service being targeted. 

The chosen exploit must then be paired with a suitable payload, usually shellcode, before executing. In the example I used the `exploit/multi/handler` module along with meterpreter reverse_tcp to gain access to the target machine. Meterpreter is an interactive shell that resides entirely in memory, writes nothing to disk and creates no new processes after being injected. It is popular for these reasons as it leaves limited evidence and impact on the machine.

Once on a target machine, Metasploit's quiver contains a full suite of post-exploitation tools, including privilege escalation, pass the hash, packet sniffing, screen capture, keyloggers, and pivoting tools. You can also set up a persistent backdoor in case the machine in question gets rebooted.

More and more features are being added to Metasploit every year, include a fuzzer to identify potential security flaws in binaries, as well as a long list of auxiliary modules too long to list here.

This is only a high-level view of what Metasploit can do. The framework is modular and easily extensible and enjoys an active community. If it doesn't do exactly what you want it to do, you can almost certainly tweak it to suit.
