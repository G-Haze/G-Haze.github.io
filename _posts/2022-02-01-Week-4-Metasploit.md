```
published:false
```

## IoC Skills Bootcamp Week 4 - Metasploit

This week we looked at another very commonly used offensive security testing tool, the Metasploit Framework, that can be used to deploy known attack vectors (CVEs) against target machines. 

Metasploit consists of six core modules that make up the majority of the tools available; Auxilliary, Exploit, Post, Encoders, Payload, and NOP. These modules can be associated with the various stages of the Lockheed Martin Cyber Kill Chain.

We can begin gathering information on the target machine by using db_nmap. This works the same as nmap but will store the results into the postgresql database which can be referred back in later phases of the pentest. We can also make use of many Auxiliary modules for scanning, fuzzing, sniffing etc. It is also possible to save the results from any port scanning and vulnerability scanning into the postgresql database for use in the later phases of the pentest.


Exploits are given rankings ranging from Low to Excellent based on how reliable they are. It details which Operating System, Service and Version. 

During the information gathering phase of a pentest, Metasploit integrates seamlessly with Nmap, SNMP scanning and Windows patch enumeration, among others. Pretty much every reconnaissance tool you can think of integrates with Metasploit, making it possible to find the chink in the armor you're looking for.

Once you've identified a weakness, hunt through Metasploit's large and extensible database for the exploit that will crack open that chink and get you in. For instance, NSA's EternalBlue exploit, released by the Shadow Brokers in 2017, has been packaged for Metasploit and is a reliable go-to when dealing with unpatched legacy Windows systems.

Like fine wine and cheese, pair the exploit with a payload to suit the task at hand. Since what most folks are wanting is a shell, a suitable payload when attacking Windows systems is the ever-popular Meterpreter, an in-memory-only interactive shell. Linux boxes get their own shellcode, depending on the exploit used.

Once on a target machine, Metasploit's quiver contains a full suite of post-exploitation tools, including privilege escalation, pass the hash, packet sniffing, screen capture, keyloggers, and pivoting tools. You can also set up a persistent backdoor in case the machine in question gets rebooted.

More and more features are being added to Metasploit every year, include a fuzzer to identify potential security flaws in binaries, as well as a long list of auxiliary modules too long to list here.

This is only a high-level view of what Metasploit can do. The framework is modular and easily extensible and enjoys an active community. If it doesn't do exactly what you want it to do, you can almost certainly tweak it to suit.
