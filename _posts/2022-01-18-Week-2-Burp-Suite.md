## IoC Skills Bootcamp Week 2 - OWASP Juice Shop

Organisations often ask for a “vulnerability assessment” or a “penetration test” of their systems. A vulnerability assessment is a systematic approach to examining core assets and measuring whether they pose a threat to the organisation against a set of criteria. A penetration test is where an “attacker” will attempt to gain access to a system and document their process for achieving this.

This week we had a look at the OWASP Juice Shop. Every three to four years, [OWASP](https://owasp.org/) (Open Web Application Security Project) publish their Top 10 Web vulnerabilities and the Juice Shop exercise is designed to showcase these. These vulnerabilities are commonly found in real-world web applications and can vary in their complexity to execute. In particular, the Juice Shop focused on Injection, Broken Authentication, Sensitive Data Exposure and Broken Access Control.

An injection flaw is a vulnerability which allows an attacker to relay malicious code through an application to another system. This can include compromising both backend systems as well as other clients connected to the vulnerable application. Some common examples of injections include:

SQL Injection - where an attacker enters a malicious or malformed SQL query to either retrieve or tamper with data from a database and sometimes log into accounts. I was able to perform one of these in the OWASP Juice Shop task using Burp Suite's Interceptor. Adding a simple statement to the http request on the login page `{"email":"' or 1=1--","password":"test"}` allowed me to log in to the account with user id 0 (the admin account in this case). This is because with the addition of `or 1=1` the email parameter will always return as true and the double dash `--` causes the server to disregard the password check.

Cross Site Scripting (XSS) - where malicious scripts are injected into otherwise benign and trusted websites. The scripts are then executed in other users browsers when they access the website/resource that was used in the attack. 

There are three main types of XSS attacks;
Stored XSS attacks - where the injected script is stored on the target servers and the victim then retrieves the malicious script from the server when it requests the stored information. 
Reflected XSS attacks - javascript that is run on the client-side of the web application. Relies on the victim clicking These are most commonly found when the server doesn't sanitise search data. 
DOM XSS attacks (Document Object Model-based) - 

Broken Authentication attacks aim to take over one or more accounts giving the attacker the same privileges as the attacked user. Authentication is “broken” when attackers are able to compromise passwords, keys or session tokens, user account information, and other details to assume user identities. Firstly, after spotting the admin's email address on one of the reviews I was able to use Burp Suite to brute-force their password. This didn't take too long using a Sniper Attack with one of the default wordlists. I was also able to reset another user's password from information left by them in their comments. 

Sensitive Data Exposure occurs when a web application, company, or other entity unknowingly exposes sensitive data. For example in the OWASP juice shop task I was able to access confidential documents as the library they were stored in was accessible to anyone. For security the library only allowed `.md` and `.pdf` files to be downloaded
by its users. However, I was able to get around this by adding a **Poison Null Bytee** into the URL. Placing a null character before the file extension told the server to teminate the string at that point therefore it was unable to check what type of file was being downloaded. This worked as the validation check was only performed on the client side and not on the back end.

Conclusion

I learnt about some common web application vulnerabilities and got to familiarise myself with some of the functionality of Burp Suite. I got some more experience brute-forcing account credentials with Sniper Attacks through the Burp Intruder tab. I learnt how to intercept http requests from websites and practiced some simple manipulations. 



As usual, I began by doing some reconnaissance on the website to find any information that may prove useful. The first thing I noticed was that the product reviews on the site showed the reviewer's email address, and even better, one of these was the admin's account. There was also a user review that referenced a TV show "Star Trek" which may come in handy. The second potential vulnerability I found was that the search function used a parameter of `q` which may be open to manipulation if user inputs aren't sanitised correctly.  

Command Injection - when web applications take input or user-controlled data and run them as system commands. An attacker may tamper with this data to execute their own system commands. 
Email injection - a security vulnerability that allows malicious users to send email messages without prior authorization by the email server. These occur when the attacker adds extra data to fields, which are not interpreted by the server correctly. 
