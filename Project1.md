## Project 1: Live Cyber Attacks of the World (Honeypot)

# Project Objective
The objective of this project was to create a live monitoring system for cyber attacks around the world using a honeypot setup. By configuring an intentionally discoverable virtual machine (VM) in Azure, the aim was to capture and analyze real-time attack data to gain insights into the geographic distribution and magnitude of cyber threats. The project aimed to enhance threat intelligence and incident response capabilities by leveraging cloud-based tools and automation to collect, analyze, and visualize attack data.

# Tools
1. Azure Cloud Platform: Utilized Azure services such as Virtual Machines, Log Analytics Workspace, and Azure Sentinel for hosting, log ingestion, and security analytics.
2. PowerShell: Developed custom PowerShell scripts to extract metadata from Windows Event Viewer and forward it to a third-party API for geolocation data retrieval.
3. Log Analytics Workspace: Configured to ingest custom logs containing geographic information and perform log analysis.
4. Azure Sentinel: Microsoft's cloud SIEM (Security Information and Event Management) platform is used for threat detection, investigation, and response.
5. Azure Sentinel Workbook: Configured to create visualizations, including a global attack map, to display real-time attack data based on physical location and attack magnitude.

# Skills Gained
1. Cloud Computing: Acquired hands-on experience in deploying and configuring resources in the Azure cloud platform, including virtual machines and log analytics workspace.
2. Log Analysis: Developed proficiency in analyzing custom logs and extracting relevant information to gain insights into cyber threats.
3. Scripting: Enhanced scripting skills through the development of custom PowerShell scripts to automate data extraction and forwarding processes.
4. Automation: Utilized automation techniques to streamline data collection and analysis processes, improving efficiency and scalability.
5. System Architecture: Gained experience in designing and implementing a system architecture for real-time monitoring and analysis of cyber attacks, including the integration of multiple Azure services for data ingestion, processing, and visualization.

# Outcomes
1. Signed up for Azure
![1](https://github.com/capital-e/My-Portfolio/assets/48088449/2cf2d03e-e5c0-498c-8983-b6e5dbf4c173)


2. Created a Windows 10 VM which will sit on the Internet and be exposed. We want it to be super discoverable, and to do that I disabled firewalls. So this will be our honeypot. Yummyy
![2](https://github.com/capital-e/My-Portfolio/assets/48088449/09434509-1b5a-46b3-9a43-652e611e8598)


3. Created a log analytics workspace to ingest logs from our VM. Azure sentinel will collect logs from this workspace and display them over the world map.
![3](https://github.com/capital-e/My-Portfolio/assets/48088449/2514f5da-41e3-4c69-9990-98beb37ec3e3)


4. Next, I had to enable the ability to collect logs from the VM into the log analytics workspace. I used “Microsoft Defender for Cloud” for this task.
![4](https://github.com/capital-e/My-Portfolio/assets/48088449/50420451-a8f2-48f4-b91b-8ba38293f23a)


5. Now it’s time to go back to the log analytics workspace and connect it to our VM.
![5](https://github.com/capital-e/My-Portfolio/assets/48088449/15691620-8692-40f6-bf81-c8d79d5ef35d)


6. Now it’s time to set up Sentinel, this is what we will use to visualize the attack data.
![6](https://github.com/capital-e/My-Portfolio/assets/48088449/42ba4044-6047-4a20-8bcb-26e42b8fa7b3)


7. The next step I performed was to connect to my VM, I noted the public IP address and connection through RDP on my own computer.
![7](https://github.com/capital-e/My-Portfolio/assets/48088449/e759fac0-f7ae-49e7-9ce7-0caca0499f5f)
![7 1](https://github.com/capital-e/My-Portfolio/assets/48088449/4adeb9ff-78a1-475d-ae77-0ae6767f082f)


8. I tried a ping to this VM from my computer and it timed out so I had to go ahead and disable the host-based firewall on Windows and the ping went through.
![8](https://github.com/capital-e/My-Portfolio/assets/48088449/54f92b8d-33b0-4867-aca9-c47796c0cc40)
![8 1](https://github.com/capital-e/My-Portfolio/assets/48088449/96c33cad-ab13-4d67-a5b0-508c49acae34)
![8 2](https://github.com/capital-e/My-Portfolio/assets/48088449/7db7ae8a-99df-47bc-82e9-8f5af57c1908)

9. Then I put my custom Powershell script in Windows Powershell ISE and saved it to the desktop in my VM. This script goes into the security events of the VM and extracts the IP address of failed login attempts and with the help of an API key from ipgeolocation.io, it will collect the geographical location data and input a new log file on the VM. Pretty interesting!
![9](https://github.com/capital-e/My-Portfolio/assets/48088449/f2b24188-069b-44e3-948f-6ad02ce1c57b)


10. I signed up to ipgeolocation and got my API key which I will insert into the Powershell script and run it to start detecting live login attempts.
![10](https://github.com/capital-e/My-Portfolio/assets/48088449/9370fb2c-a637-47bd-b515-7c5c65dfe1c7)
![10 1](https://github.com/capital-e/My-Portfolio/assets/48088449/337cc7aa-8b24-47ad-b01c-d92decba4d50)
![10 2](https://github.com/capital-e/My-Portfolio/assets/48088449/361cdcc0-aa79-4084-8aa2-45e2558fcfc2)


11. Time to create a custom log inside the log analytics workspace to allow us to bring the new logs with geolocation in. I ran a query to view my logs and it was successful.
![11](https://github.com/capital-e/My-Portfolio/assets/48088449/5b23dc06-ffee-49c7-a37c-af4b0e1253bf)
![11 1](https://github.com/capital-e/My-Portfolio/assets/48088449/a5706972-854c-4ff7-b602-0cee6c2d71a2)


12. Next I needed to extract the individual fields(country, ip, longitude, latitude etc.) from the raw data in the ingested logs. This took a while. I pushed through and now my logs look more readable and clean.
![12](https://github.com/capital-e/My-Portfolio/assets/48088449/2c178aee-6c01-4c79-a7cf-ed2e2a724d22)


13. Now it’s finally time to set up our map. Let’s see where our attacks are coming from. For this step, I ran my query again in a Sentinel work and chose the setting to display my output on a map. After a few hours, I had a whole lot of attack attempts.
![13](https://github.com/capital-e/My-Portfolio/assets/48088449/6fe8911e-77b0-4eb2-ad94-82440ccdfd73)
![13 1](https://github.com/capital-e/My-Portfolio/assets/48088449/0cb02b98-c418-49e1-a21d-b0bdec8cd5a8)
<img width="1280" alt="13 2" src="https://github.com/capital-e/My-Portfolio/assets/48088449/4a4fa268-8c33-454e-8847-bb94692b48cc">


This cybersecurity lab exemplifies a proactive approach to threat detection and mitigation. By creating a honeypot environment with a Windows 10 VM and intentionally disabling firewalls, I simulated an attractive target for potential attackers. Leveraging Azure services such as Log Analytics Workspace and Sentinel, I established a robust monitoring system to collect and analyze security logs in real time. Integration with Microsoft Defender for Cloud further enhanced log collection capabilities. Through the development of a custom PowerShell script, coupled with the ipgeolocation.io API, I was able to extract and analyze failed login attempts, gaining valuable insights into potential threats and their geographical origins. By visualizing attack data on a world map, I gained a comprehensive understanding of the threat landscape and empowered myself to proactively defend against cyber threats. This lab underscores the importance of continuous monitoring, threat intelligence, and proactive defence strategies in safeguarding against evolving cybersecurity threats.


