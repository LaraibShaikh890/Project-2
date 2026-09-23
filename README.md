# Project-2

PENETRATION TESTING REPORT
FOOTPRINTING & NETWORK SCANNING PHASES
W2-PM-FINAL | CYBERSECURITY |  NETWORKWALKS

This is Week 2 of my Cybersecurity & Ethical Hacking internship, I completed hands-on work in footprinting, reconnaissance and network scanning.

In the footprinting exercise, I used six Kali Linux tools to gather information about the target domain. WHOIS supplied registration details, WhatWeb fingerprinted the web technologies, Nslookup resolved the domain to an IP address, Curl exposed the HTTP headers, Wafw00f detected the firewall, and DNSRecon revealed further DNS information.
In the scanning exercise, I used Zenmap to determine my local network setup and find active hosts. I also recorded IP and MAC address details and generated a network topology map.

These exercises showed me how much information gathering matters in security. Before any attempt at exploitation, a professional can learn a great deal about an environment just by studying public information and how systems respond on the network.

I also learned the value of clear documentation. A good security report explains what was done, what was found, what the finding means, what risk it creates, and how that risk can be reduced.

Finally, I learned that reconnaissance and scanning must stay within an authorized scope. All of this work was done as part of the assigned educational lab.


1. Legal Notice:
Everything in this report was done only on systems and devices I own or where I received written authorization beforehand. The material is shared strictly for learning and research. Please don’t use it to break any law. The instructor, the authors, and Networkwalks take no responsibility for how anyone applies this knowledge, and each person answers for their own actions. Misuse can lead to criminal charges, large fines, job loss, and a lasting criminal record. In most countries, accessing a system without permission is a crime even if no damage occurs.

   
2. Introduction:
This report documents two hands-on exercises from Week 2 of my internship at Networkwalks. The first (W2-PM1) is a footprinting exercise against the networkwalks.com domain using several Kali Linux tools. The second (W2-PM5) is a scan of my own home network using Zenmap. Together they follow the path an attacker typically takes: first collecting publicly available information, then identifying which hosts on a network are active.
   
Footprinting was carried out in Kali Linux, and scanning was done from a Windows PC running Zenmap. For each step I list the exact command, what it returned, a screenshot as proof, and a brief explanation of why the result would matter to an attacker.

3. Activities Performed:
I carried out reconnaissance on networkwalks.com with six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each tool exposed a different layer of information about the target.

I began with WHOIS to pull the public registration record for the domain, which also revealed its name servers. This gave a picture of how the domain is registered and where it is hosted.
Next, WhatWeb fingerprinted the technologies running on the site. It detected WordPress 7.0.4 and the WP Download Manager plugin at version 3.3.58, plus other details the site leaks.

Nslookup then translated the domain name into its IP address. 

With Curl and the -I flag, I fetched only the HTTP response headers. They disclosed more about the web application and showed that the WordPress REST API endpoint, /wp-json/, is publicly reachable.

I then ran Wafw00f to check whether a Web Application Firewall sits in front of the site. It detected ModSecurity (SpiderLabs).
Last, DNSRecon enumerated the domain’s DNS records. It returned the name servers, mail servers, SPF/TXT records, service (SRV) records and details about the DNS software in use.

For the second activity, I used Zenmap to run network discovery on my local network. The practical asked me to find my local IP address and subnet, discover live hosts, record their IP and MAC addresses, and generate a network topology.

I started with the Windows ipconfig command to find my local IP address and LAN subnet. I then entered that subnet into Zenmap and chose the Ping Scan profile to find active hosts.
The results given in the practical showed one live host. 

Once the scan finished, I opened the Topology tab in Zenmap, turned on the legend, and saved the network topology as a PDF, as the practical required.





<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/3fbfd118-8e43-45aa-9f45-2f8cd2f5ed9e" />





4. Recommendations:
Based on what these exercises showed, I suggest the following security improvements:
•	Limit exposed technology details: Regularly check what a visitor can learn about the site’s web stack, CMS and plugins, and hide what isn’t needed.

•	Patch consistently: Keep the CMS, plugins and other components up to date, and compare them against current security advisories.

•	Trim HTTP headers: Review response headers and remove technical details that give nothing to legitimate users.

•	Audit DNS records: Check DNS periodically so that only necessary records and services are visible to the public.

•	Maintain the WAF: Keep ModSecurity switched on and tuned, since it already stops basic attacks.

•	Scan your own network: Run internal discovery scans on a schedule to know which devices are active.

•	Follow up on unfamiliar devices: Investigate and verify anything unexpected that shows up in a scan.

•	Keep network documentation current: Record the topology and device details, and update them when things change.

•	Test only with permission: Run reconnaissance and scanning only on systems and networks where you have clear authorization.
