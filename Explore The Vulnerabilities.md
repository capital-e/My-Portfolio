## Project 2: Explore The Vulnerabilities

# Project Objective
The objective of this project was to create a hands-on learning environment for exploring and understanding cybersecurity vulnerabilities through ethical hacking exercises. By setting up a virtual home lab environment using VirtualBox, the project aimed to provide a safe and controlled space for practising penetration testing techniques and simulating real-world attack scenarios. Using Kali Linux as the attack system and Metasploitable 2 as the target, the project sought to develop practical skills in identifying, exploiting, and mitigating security weaknesses to strengthen overall cybersecurity posture.

# Tools
1. VirtualBox: Utilized for creating a virtualized home lab environment to simulate networked systems for ethical hacking purposes.
2. Kali Linux: Used as the primary operating system for conducting penetration testing and ethical hacking activities, equipped with a wide range of pre-installed security tools.
3. Metasploitable 2: Configured as the target system to practice exploiting vulnerabilities and conducting penetration testing exercises.
4. Metasploit Framework: Leveraged for developing and executing exploits against vulnerable systems, enhancing proficiency in penetration testing methodologies.
5. Nmap: Employed for network reconnaissance and scanning to identify open ports, services, and potential attack vectors within the target environment.
6. Wireshark: Utilized for network traffic analysis to capture and analyze packet data, facilitating the identification of suspicious or malicious activity.

# Skills Gained
1. Vulnerability Assessment: Developed skills in identifying and assessing vulnerabilities within target systems through active reconnaissance and scanning techniques.
2. Network Traffic Analysis: Enhanced proficiency in analyzing network traffic using Wireshark to identify anomalies, potential security threats, and malicious activity.
3. Penetration Testing: Acquired hands-on experience in conducting penetration tests to identify and exploit security weaknesses in target systems, utilizing tools such as Metasploit and Nmap.
4. Ethical Hacking: Developed a solid foundation in ethical hacking principles and techniques, including reconnaissance, exploitation, post-exploitation, and reporting.
5. Documentation: Improved skills in documenting findings, vulnerabilities, and recommended solutions to enhance security awareness and facilitate the remediation of identified risks.

# Outcomes
1. Metasploitable 2 is up and running in my Virtualbox
![1](https://github.com/capital-e/My-Portfolio/assets/48088449/0789f508-18dd-4994-96b6-35a4de129427)


2. I used the netdiscover tool in Kali to detect the IP address of the metasploitable VM. I could have signed in to metasploitable and used the ifconfig command but I want to simulate a real-world scenario as much as possible. I’m assuming the IP address I’m looking for is the last one. I will run an Nmap scan to verify. I decided to store the output of the scan in a text file so I could easily make reference to it without having to perform the scan all over again. As you can see, that’s a LOT of open ports.
![2](https://github.com/capital-e/My-Portfolio/assets/48088449/b4f3e5a3-ad01-4cb1-81e4-e2a8671d530b)
![2 1](https://github.com/capital-e/My-Portfolio/assets/48088449/90f92fae-a2f2-4784-9ef1-3d5da460f9ac)


3. I will exploit port 21 (FTP) first. For this, I will start by using the tool searchsploit to find out if there’s an exploit for this specific FTP version number. I found a Metasploit exploit so I must look into the msfconsole for this one. Note that I will be using the msfconsole throughout this hacking lab.
![3](https://github.com/capital-e/My-Portfolio/assets/48088449/2cbf569d-f210-4430-aa2a-de64a9b4caa6)
![3 1](https://github.com/capital-e/My-Portfolio/assets/48088449/bd470c4b-5f82-4e94-ad2b-68812cf7a369)


4. I found the exploit in msfconsole, I used it and set rhosts to my metasploitable IP address and finally ran the exploit and successfully found a shell and I was in. I even had root access.
![4](https://github.com/capital-e/My-Portfolio/assets/48088449/df480311-ebd5-44e4-827d-4f84c198d7b2)
![4 1](https://github.com/capital-e/My-Portfolio/assets/48088449/c0e5b8ac-647b-4ff6-a5eb-17860f120439)


5. Next we will exploit ssh. For this one, we need a username list file and a password list file. We will set some other options to successfully get a shell. Works perfectly!
![5](https://github.com/capital-e/My-Portfolio/assets/48088449/a65bf494-c0e9-4769-93ee-75cfbd4f437a)
![5 1](https://github.com/capital-e/My-Portfolio/assets/48088449/f37c436e-a9d4-4afb-9493-7914e3c03c3d)


6. Next we will exploit Telnet. We will use the same username file and password file to exploit this. Basically, it is the same process with ssh. Note that I used Wireshark in this section to capture traffic while I used the command “Telnet 10.0.1.6” and inputted some credentials. These credentials appeared as clear text in the packet capture file. I did this just for practice and it did not play a role in successfully exploiting this protocol which is why I did not include wireshark screenshots.
![6](https://github.com/capital-e/My-Portfolio/assets/48088449/920717e2-b3df-4243-86cd-8b78e1c9cec1)


7. Let us exploit port 25 smtp next. With this port, we will use the msfconsole to enumerate the users available on the mail server in metasploitable.
![7](https://github.com/capital-e/My-Portfolio/assets/48088449/6f536fb7-8abe-47b9-8722-64906856021e)


8. Next, let’s check out port 80 http. First, we will use msfconsole to find more information about the HTTP version and then use that information to exploit it. We found out that the HTTP server was powered by PHP and that’s very important information we can use to find our exploit.
![8](https://github.com/capital-e/My-Portfolio/assets/48088449/de07a7f7-6d54-4edc-b4fa-296830dbb682)
![8 1](https://github.com/capital-e/My-Portfolio/assets/48088449/b7192875-6622-40ca-819f-fc3ef03e17f9)


9. Next we will exploit port 5900 VNC. We will use msfconsole to find some login credentials and then finally use those credentials to login remotely to the server. I set a default username “root” and msfconsole run it against a password list and found the password: “password”.
![9](https://github.com/capital-e/My-Portfolio/assets/48088449/2d5a852d-89f1-4b8b-9cea-323ca2ec1add)
![9 1](https://github.com/capital-e/My-Portfolio/assets/48088449/53393a9d-cffe-402a-86b3-8603a29a3a7e)
![9 2](https://github.com/capital-e/My-Portfolio/assets/48088449/4d7a55e9-f943-4259-bbf3-24048146b411)


This project demonstrates a hands-on approach to cybersecurity through the practical exploitation of vulnerabilities in a simulated environment. By utilizing tools like Nmap, searchsploit, and Metasploit, I systematically identified and exploited various services and ports on a vulnerable machine, Metasploitable 2. Through exploiting FTP, SSH, Telnet, SMTP, HTTP, and VNC services, I gained unauthorized access, demonstrating the potential risks posed by unsecured network services. This project underscores the importance of rigorous security measures, including regular vulnerability assessments, patch management, and secure configuration practices, to mitigate the risk of unauthorized access and data breaches. Additionally, it highlights the significance of ethical hacking and penetration testing as essential components of a robust cybersecurity strategy, allowing organizations to proactively identify and remediate vulnerabilities before they are exploited by malicious actors.
