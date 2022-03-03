## IoC Skills Bootcamp Week 4 - Metasploit

This week we looked at another very commonly used offensive security testing tool, the Metasploit Framework, that can be used to probe vulnerabilities on networks and servers and deploy known attack vectors (CVEs) against them. As usual, to aid with our learning we would be completing the [Metasploit](https://tryhackme.com/room/rpmetasploit) room on tryhackme.

Metasploit consists of six core modules that make up the majority of the tools available; Auxilliary, Exploit, Post, Encoders, Payload, and NOP. These modules can be associated with the various stages of the Lockheed Martin Cyber Kill Chain. They cover an extremely broad range of functions against many systems ranging from Linux and Windows enumeration to modules that act as an [Amazon Fire TV Remote Control](https://www.infosecmatter.com/metasploit-module-library/?mm=auxiliary/admin/firetv/firetv_youtube).

We can begin gathering information on the target machine by using `db_nmap`. This works the same as nmap but will store the results into the postgresql database which can be referred back to when required. It is also possible to import any port or vulnerability scan results into the database by using `db_import`. To perform further reconnaissance we could choose use of one the many auxiliary modules packaged with Metasploit for scanning, fuzzing or sniffing if suitable. Auxiliary modules are not exploits but interesting features that may be useful to the attacker.

After gathering sufficient information to identify a weakness, we can search through Metasploit's vast and extensible database for an appropriate exploit. Exploits within Metasploit are given rankings ranging from Low to Excellent based on how reliable they are and whether they are likely to crash the service being targeted. 

The chosen exploit must then be paired with a suitable payload, usually shellcode, before executing. In the example I used the `exploit/multi/handler` module, a generic payload handler, along with meterpreter reverse_tcp to gain a reverse shell on the target machine. Meterpreter is an interactive shell that resides entirely in memory, writes nothing to disk and creates no new processes after being injected. It is popular for these reasons as it leaves limited evidence and impact on the machine.

Once we have access to the system we can make use of Metasploit's many post-exploitation tools. These include privilege escalation methods, pass the hash techniques, packet sniffers, screen captures, keyloggers and pivoting tools. It is also possible to set up a persistent backdoor in case the machine gets restarted and we need continued access.

### Conclusion

Metasploit is an extremely valuable tool when performing a pentest and it's arsenal grows each year with more and more modules added to it. As it is open-source and has a large, active community there are many tweaks available for the product. For example, Armitage is a GUI front-end for the Metasploit framework which can be used instead of the usual command line interface through `msfconsole`. However, I am yet to try this as I am focusing on getting more familiar with the terminal commands. I also plan to have a go at some capture the flag exercises to practice what I have learnt today so I'm sure we will see some more blog posts on Metasploit in the future.  
