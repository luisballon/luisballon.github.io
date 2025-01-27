---
title: Clase 9 - Advanced Persistent Threats (APTs)
date: 2024-11-07 00:20:00 -0500
categories: [Cybersecurity,Ethical Hacking,Pentesting,Exploitation Techniques]
tags: [elasticsearch, soluciones siem]     # TAG names should always be lowercase
---

<!-- <hr style="border: none; height: 10px; background-color: #003b00;" />

# <font color="#87CEEB">Examen Parcial.</font>

<hr style="border: none; height: 10px; background-color: #003b00;" /> -->

## Current networks and typical threats per layer

![alt text](/assets/images/current-architectural-networks.png)
_**Paper**: "Comprehensive Survey on AI-based technologies for enhancing IoT privacy and security: Trends, Challenges, and Solutions"   
[https://hcisj.com/data/file/article/2023080005/13-39.pdf](https://hcisj.com/data/file/article/2023080005/13-39.pdf)_

## Real Cases of Advanced Persistent Threat (APT) Attacks on Cyber-Physical Systems. 

- Since 2010, with Stuxnet Worm, APTs and Cyber-warfare over Cyber-Physical Systems are a major concern on Cybersecurity.
- Plenty of number of known examples to describe a critical situation. And there are more that remain non-disclosed.

| Year  | Attack Name                | Target/System Affected                                    |
|-------|----------------------------|-----------------------------------------------------------|
| 2010  | Stuxnet Worm               | Iranian Nuclear CPS                                       |
| 2015  | BlackEnergy Malware        | Ukrainian Power Grid                                      |
| 2016  | CrashOverride Malware      | Ukrainian Power Grid                                      |
| 2017  | Triton Malware             | Petrochemical plant in Saudi Arabia                       |
| 2017  | NotPetya Ransomware        | Cyber-physical systems of Maersk and Merck                |
| 2021  | Oldsmar APT                | Chemical levels in the water plant supply (US)            |
| 2021  | Colonial Pipeline Ransomware | Fuel pipelines in the US                                |
| 2021  | Water Sector Attacks       | Chemical levels in water treatment facilities (US)        |
| 2021  | Iranian Railway System Attack | Iran's railway system                                  |

## So, how is the research towards Intrusion Detection Systems?

- Intrusion Detection Systems, or IDS in short, are systems design to detect cyber-attacks, **including APTs**.
- State-of-the-art IDS are, of course, AI & Big Data-driven.
- The following picture is modified from the original to describe the most relevant stages regarding how researchers propose or improve new technologies for IDS. We just added dotted-line-boxes and add some labels for a better depiction of the stages.

![alt text](/assets/images/research-trends-ids-1.png)
_**Paper**: "Learn-IDS: Bridging Gaps between Datasets and Learning-Based Network Intrusion Detection"
[https://doi.org/10.3390/electronics13061072](https://doi.org/10.3390/electronics13061072)_

- Basically, researchers employ public datasets containing some form of network information where attacks happen. Then, there is a raw-data pre-processing stage in which the different datasets are conditioned and uniformly formatted for the next stages. Next stage is Data Customizing in which features are extracted following a tabular, time-series, array, or graph formats. These features subsequently are input into the IDS AI-model in which the model is trained and evaluated.

- So, continuing with the following picture, as easy to deduce, researchers efforts are targeting new technologies and algorithms for the Pre-processing stage and the Model-related stages.
    - Novel data-pipeline techniques are being proposed in the pre-processing stage.
    - Novel feature selection methods, novel deep-learning and/or deep-reinforcement-learning models, and novel optimization techniques are being proposed for the modelling stage.

![alt text](/assets/images/research-trends-ids-2.png)
_**Paper**: "Learn-IDS: Bridging Gaps between Datasets and Learning-Based Network Intrusion Detection"
[https://doi.org/10.3390/electronics13061072](https://doi.org/10.3390/electronics13061072)_

<!-- - However, **researchers are still relying on datasets which:** 
    - Most of the time only considers **one type of data (network traffic, pcap)** 
    - Most of the attacks are **isolated attacks**, meaning that there is not strong correlation between them. Unlike ATP attacks, in which each action in the target system or network is meaningful.
    - These datasets need Labeling, which is time and effort consuming.
    - And most of the real APT attack datasets are Not available because of the non-disclose politics of the affected organization. -->

## Problem Statement

- However, despite advancements in intrusion detection systems, researchers continue to face significant challenges due to limitations in the datasets being used:

    - **Most existing datasets focus on a single data type**, such as network traffic or PCAP files, which limits the comprehensiveness of the analysis.
    - **Attacks within these datasets are often isolated**, lacking the complex, multi-stage correlations found in Advanced Persistent Threat (APT) attacks. In APTs, every action across the network or system carries a strategic significance, unlike in isolated attack scenarios.
    - **Dataset labeling remains a time-consuming and labor-intensive process**, requiring extensive manual effort to ensure accuracy.
    + **Real-world APT datasets are generally unavailable due to non-disclosure policies** enforced by affected organizations, making it difficult to develop solutions based on real, high-impact incidents.

![alt text](/assets/images/research-trends-ids-3.png)
_**Paper**: "Learn-IDS: Bridging Gaps between Datasets and Learning-Based Network Intrusion Detection"
[https://doi.org/10.3390/electronics13061072](https://doi.org/10.3390/electronics13061072)_


## Stuxnet

### The Genesis and Initial Deployment (2007–2009)

- **Early Development**: Stuxnet was meticulously crafted as a weaponized form of malware aimed specifically at industrial control systems (ICS). Development is believed to have begun in the early 2000s, with initial deployments starting as early as November 2007​.

- **Target Selection**: Its main target was a specific ICS setup—Siemens SIMATIC WinCC and PCS7 software along with certain Siemens S7 PLCs (Programmable Logic Controllers). These controlled the centrifuges used in uranium enrichment, indicating a strategic focus on Iran’s nuclear program.

### Discovery of Stuxnet (2010)

- **2010, Summer**: Widespread discussions about Stuxnet only began after it was detected by cybersecurity researchers in 2010. The Industrial Control Systems Cyber Emergency Response Team (ICS-CERT) issued an advisory, confirming its presence and detailing its advanced capabilities​.

- **Propagation and Detection**: By this time, Stuxnet had spread to 100,000 computers across various countries, although it was programmed to seek out a very specific type of configuration, which significantly limited its payload’s activation.

### Attack Mechanisms and Methods

- **Zero-Day Exploits**: Stuxnet utilized four zero-day vulnerabilities in Windows, allowing it to bypass standard security controls and spread undetected through Windows networks from Windows 2000 to Windows 7​.

- **Propagation Techniques**: Stuxnet spread via multiple methods:
    - **USB drives** were used to introduce the malware to isolated networks (air-gapped systems).
    - **Network shares and print services** on Windows devices allowed it to spread across corporate networks.
    - **Database Infiltration**: The malware exploited default credentials in SQL Server on the Siemens WinCC database, embedding itself deeper into targeted systems.

- **Targeted PLC Manipulation**: Once within a compatible Siemens control system, Stuxnet:

    - **Overwrote critical drivers** to enable a man-in-the-middle (MitM) attack. This allowed it to manipulate PLC operations while hiding its presence.

    - **Injected malicious code** into PLCs to control centrifuge speeds, altering them in a destructive pattern that would damage the machinery without triggering immediate alarms.

### Execution of the Payload

- **Frequency Manipulation**: Once Stuxnet found the desired PLC setup, it manipulated the centrifuges' frequencies, alternating speeds to stress and degrade the hardware over time. This led to mechanical failures that hindered uranium enrichment efforts.
    
- **Stealth and Persistence**: The malware acted as a rootkit on both Windows and PLC systems, masking its activity and reporting normal operations to operators, who would remain unaware of the ongoing sabotage​.

### Detection and Aftermath

- **Response and Media Attention**: After the malware was uncovered and publicized, Siemens issued a security advisory and tools to detect and remove Stuxnet. The event drew global attention to the potential for cyber-attacks on critical infrastructure, making it clear that industrial networks were vulnerable​.

- **Lessons Learned**: Stuxnet’s success demonstrated the need for heightened security measures in ICS environments, prompting a shift in cybersecurity practices. Industry leaders began implementing more network segmentation, zero-trust principles, and ICS-specific security tools to prevent similar attacks in the future.

![alt text](/assets/images/stuxnet-infection-process.png)
_**Paper**: "Stuxnet's infection processes"
[Hacking Industrial Control Systems](https://www.sciencedirect.com/book/9780124201149/industrial-network-security)_