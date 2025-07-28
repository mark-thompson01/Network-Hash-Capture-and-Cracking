# Network-Hash-Capture-and-Cracking

This repository is based on the Network Hash Capture and Cracking with Responder and Hashcat on my GitHub webpages portfolio. This lab demonstration outlines the process of using Responder to capture an NTLMv2 hash from a Windows 10 host over the network and then cracking the captured hash with Hashcat to expose the password. This lab was conducted in a segmented LAN environment for testing purposes. 


---


## Lab Setup
The lab environment consists of the following setup:

> **Segmented Broadcast Domain:** For this lab setup, I setup a broadcast domain to complete isolate a Kali VM and standard Windows 10 PC.
> **Kali Linux VM:** Used for running Responder to capture the NTLMv2 hash and using Hashcat to crack the hash.
> **Windows 10 Desktop:** Used as the victim machine to capture the NTLMv2 hash. 

The environment was set up with isolation using network segmentation techniques. Never run these tools without obtaining authorization from the network or domain administrator.




## 🖥️ **Live Project Webpage:**  
👉 [Network Hash Capture and Cracking](https://mark-thompson01.github.io/MTPortfolio/Lab%20Projects/Network%20Hash%20Capture%20and%20Cracking/)


---


## 🛠️ Tech Used
- Segmented broadcast domain
- Oracle VirtualBox
- Kali Linux VM
- Windows 10 PC
- Responder
- Hashcat


---


## 🔁 How to Recreate This Lab
- Download and install Oracle VirtualBox
- Download, install, and setup a Kali Linux VM
- Setup a Windows VM segmented or Windows 10 host on a segmented network
- Run Responder
- Try to connect to a server name that doesn't exist on the Windows host
- Capture the NTLMv2 pasword hash
- Save the hash value to a text file
- Try to crack the hash file using Hashcat to crack the password


---


## What I've Learned
Through this project, I have learned how:
- NTLMv2 (NT LAN Manager version 2) is a challenge-response network authentication protocol between a client and a server, used primarily in Windows environments.
  
- NTLMv2 employes a challenge-response process based on password hashes to verify a user's identity and grant access to network resources without transmitting the password itself.
  
- Responder exploits weaknesses in how Windows systems try to automatically authenticate to network resources.
 - Responder poisons name resolution (LLMNR/NBT-NS/MDNS spoofing)
 - In a local network, if a machine cannot resolve a hostname through DNS, it will fall back to broadcast protcols like:
     - LLMNR (Link-Local Multicast Name Resolution)
     - NBT-NS (NetBIOS Name Service)
     - mDNS (Multicast DNS)
  - Responder listens for these requests and pretends to be the host being requested (spoofs the response).
    - Believing it has found the correct server, the victim's machine tries to authenticate automatically using NTLM (Windows tries single sign-on).
    - The victim machine sends an NTLM negotiation message to Responder, resulting in the NTLMv2 hash value of the victim to be retrievd by Responder.
- Once the password hash is retrieved, you can then run hashcat to try and crack it and expose the password.
   

---



## 📁 More from Me

Visit my full GitHub Pages portfolio to explore additional projects:

🔗 [MTPortfolio – Full Project Index](https://mark-thompson01.github.io/MTPortfolio/)


---


## 📜 License

This project is licensed under the 
[Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

You are free to use, share, and adapt this content, with appropriate credit.
