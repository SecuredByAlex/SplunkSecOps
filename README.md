# SplunkSecOps


## Objective

The primary objective of this project was to simulate a real-world security incident using a TryHackMe threat hunting room, focusing on investigating a compromised host within the HR department. Leveraging Windows Event Logs (Event ID 4688) and Splunk as the SIEM tool, the project aimed to detect anomalous process executions, identify LOLBIN abuse, trace malware delivery vectors, and uncover adversary activities using behavioral analytics and event correlation. The goal was to enhance defensive detection capabilities in a segmented enterprise environment with limited forensic resources.


## Skills Learned

- Threat Hunting with Splunk – Ingested and queried logs to uncover suspicious activity.
- LOLBIN Detection (Living-off-the-Land Binaries) – Detected malicious use of certutil.exe.
- Anomaly Detection – Identified an imposter account (Amel1a) and misuse of scheduled tasks.
- Timeline Reconstruction – Traced the attack timeline to key events (e.g., 2022-03-04).
- Payload Analysis – Identified a downloaded malicious file (benign.exe) and C2 link (controlc.com).
- SIEM Use Case Creation – Demonstrated how to build queries and detect threats with limited data.
- Incident Reporting and Documentation – Documented each step of the attack chain and defensive response.


## Tools Used

- TryHackMe paltform for accessing the Lab
- Splunk: Open-source SIEM tool
- Kali Linux Terminal: Command-line interface for executing the Tool.
- Virtual Machine (VM): Simulated environment for executing tasks

  
## Scenario


One of the client’s IDS indicated a potentially suspicious process execution indicating one of the hosts from the HR department was compromised. Some tools related to network information gathering / scheduled tasks were executed which confirmed the suspicion. Due to limited resources, we could only pull the process execution logs with Event ID: 4688 and ingested them into Splunk with the index win_eventlogs for further investigation.

About the Network Information

The network is divided into three logical segments. It will help in the investigation.

IT Department

- James
- Moin
- Katrina

HR department

- Haroon
- Chris
- Diana

Marketing department

- Bell
- Amelia
- Deepak



## Steps Taken

Q1. How many logs are ingested from the month of March, 2022?<br>
Ans : 13,959<br>
O/P: <img src="https://github.com/user-attachments/assets/50fb768c-bbcc-46cf-9c1e-3444abaf8767" /> <br><br>`

Q2. Imposter Alert: There seems to be an imposter account observed in the logs, what is the name of that user?<br>
Ans : Amel1a<br>
O/P: <img src="https://github.com/user-attachments/assets/afb1c664-78a8-45d2-9a2d-ea4bfe26ad7e" /> <br><br>

Q3. Which user from the HR department was observed to be running scheduled tasks?<br>
Ans : Chris.fort<br>
O/P: <img src="https://github.com/user-attachments/assets/541b6a09-6858-4f5b-98af-a8c58bec93cf" /> <br><br>

Q4. Which user from the HR department executed a system process (LOLBIN) to download a payload from a file-sharing host.<br>
Ans : haroon<br>
O/P: <img src="https://github.com/user-attachments/assets/37abbd12-c981-44a2-ba2d-610cc483bdfd" /> 
     <img src="https://github.com/user-attachments/assets/29b15efe-1489-4739-87a5-e9f687b110ce" /> <br><br>

Q5. To bypass the security controls, which system process (lolbin) was used to download a payload from the internet?<br>
Ans : certutil.exe<br>
O/P: <img src="https://github.com/user-attachments/assets/f5aaf543-ff83-4a88-883a-e0dc7a1e2d8c" /> <br><br>

Q6. What was the date that this binary was executed by the infected host? format (YYYY-MM-DD)<br>
Ans : 2022-03-04<br>
O/P: <img src="https://github.com/user-attachments/assets/e3f8dcb0-1ac4-4898-9c52-3f477a136211" /> <br><br>

Q7. Which third-party site was accessed to download the malicious payload?<br>
Ans :controlc.com<br>
O/P: <img src="https://github.com/user-attachments/assets/6e3aea60-941b-462a-8e44-0f69b362f9a5" /> <br><br>

Q8. What is the name of the file that was saved on the host machine from the C2 server during the post-exploitation phase?<br>
Ans : benign.exe<br>
O/P: <img src="https://github.com/user-attachments/assets/a8f5202f-05f1-4e31-bd60-9e905c39a944" /> <br><br>

Q9. What is the URL that the infected host connected to?<br>
Ans : https://controlc.com/e4d11035<br>
O/P: <img src="https://github.com/user-attachments/assets/eac40299-9342-4567-a01c-8a933cd83c9b" /> <br><br>


## Conclusion 

This project provided a hands-on experience through a TryHackMe room scenario, simulating a SOC analyst’s role in detecting and investigating a potential compromise. Despite limited resources, by ingesting and analyzing only Event ID 4688 into Splunk, the investigation successfully revealed the adversary's tactics: from credential misuse (Amel1a) and scheduled tasks (chris.fort) to malicious payload delivery by haroon using certutil.exe from controlc.com. The project demonstrated how critical log visibility, structured network segmentation, and strategic Splunk queries can effectively detect and respond to threats in a real-world-inspired environment.
