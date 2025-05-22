## Project 3: Centralized Visuals (SIEM)

# Project Objective
The objective of this project was to implement a centralized Security Information and Event Management (SIEM) solution using the Elastic Stack in order to enhance security event monitoring, threat detection, and incident response capabilities. By setting up and configuring Elastic Stack SIEM in a home lab environment, the project aimed to develop practical skills in SIEM configuration and management, security event analysis, data visualization, alerting mechanisms, and incident response processes.

# Tools
1. Elastic Stack SIEM: Utilized for setting up and configuring the centralized SIEM solution, including Elasticsearch for data storage and indexing, Logstash for log ingestion and processing, and Kibana for data visualization and dashboard creation.
2. Kali Linux: Employed as the operating system for generating and analyzing security events, utilizing tools such as Nmap for network reconnaissance and scanning within the home lab environment.
3. Elastic Agents: Configured and deployed on Kali Linux VMs for log collection and forwarding to the Elastic SIEM for security event monitoring and analysis.

# Skills Gained
1. SIEM Configuration and Management: Demonstrated proficiency in setting up and configuring the Elastic Stack SIEM solution, including the deployment of Elastic Agents for log collection and forwarding, as well as the configuration of data sources and indices within Elasticsearch.
2. Security Event Analysis: Acquired hands-on experience in generating, collecting, and analyzing security events using tools such as Nmap on Kali Linux, and querying Elastic SIEM to identify and investigate security incidents.
3. Data Visualization: Developed skills in creating custom dashboards and visualizations in Kibana to effectively visualize and interpret security event data, facilitating the identification of trends, patterns, and anomalies.
4. Alerting Mechanisms: Successfully created and tested alert rules within Elastic SIEM for detecting specific security events, demonstrating competency in proactive incident response and alert management.
5. Incident Response: Enhanced skills in incident detection, investigation, and response processes through the use of centralized SIEM solution, contributing to improved security posture and resilience against cyber threats.

# Outcomes
1. Signed up for Elastic
   ![1](https://github.com/capital-e/My-Portfolio/assets/48088449/d444b921-8761-429c-b9f3-ee5eb4dec67b)


2. Kali Linux VM up and running via VirtualBox (Kali definitely has the best wallpapers, prove me wrong)
   ![2](https://github.com/capital-e/My-Portfolio/assets/48088449/b924da2d-e434-4cd7-bd1e-906b3743bf62)


3. Added an integration via Elastic Defend. Elastic Defend is set up to provide a complete EDR for my Kali Linux VM I will be linking.
   ![3](https://github.com/capital-e/My-Portfolio/assets/48088449/2f11dc3f-ca62-4757-831d-2c7bd4e1cdbb)


4. Successfully linked my Kali VM to Elastic Defend
   ![4](https://github.com/capital-e/My-Portfolio/assets/48088449/39341b7f-9257-4a62-96e1-7baa99d9b220)
   ![4 0](https://github.com/capital-e/My-Portfolio/assets/48088449/e565054f-bc1f-4392-84d9-3a5bba7faf3e)
   ![4 1](https://github.com/capital-e/My-Portfolio/assets/48088449/77b38b25-e862-43dd-853d-e6def04f0b3e)


5. I run NMAP to generate some logs, then run a query in the observability logs section in Elastic Stack
   ![5](https://github.com/capital-e/My-Portfolio/assets/48088449/95caaead-324b-44f5-b5dd-5fe59326f386)


6. Let’s visualize our logs on a chart, that’d be cool. Not the best graph lol but I like green
    ![6](https://github.com/capital-e/My-Portfolio/assets/48088449/73d20137-4f22-474d-908b-a6730dbbe57c)


7. Let’s create an alert to inform us whenever an nmap scan is run. I chose to isolate the VM as an action whenever the alert is triggered. That's a rapid incidence response right there lol.
    ![7](https://github.com/capital-e/My-Portfolio/assets/48088449/c245c6a4-9bfc-43f0-9cef-84ceb69a16dd)


8. After running some new nmap scans let’s check the outcome.
   ![8](https://github.com/capital-e/My-Portfolio/assets/48088449/aab38f83-dfeb-4108-b981-32235972d09e)
   ![8 1](https://github.com/capital-e/My-Portfolio/assets/48088449/713f0539-0a98-4874-a860-409b36546dbf)


The lab successfully integrated Elastic Defend with a Kali Linux VM, enhancing cybersecurity monitoring and incident response. Key achievements include setting up Elastic Defend, linking the Kali VM, running NMAP to generate logs, querying logs in Elastic Stack, visualizing data on a chart, and creating alerts for NMAP scans. This proactive defense strategy enables real-time visibility, centralized log management, rapid incident response, and strengthens overall security posture against potential threats.
