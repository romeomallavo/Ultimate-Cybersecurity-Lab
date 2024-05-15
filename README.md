# Ultimate Cybersecurity Lab Project

This repository contains the instructions and configuration steps to build an ultimate cybersecurity lab environment. This lab includes a variety of tools and environments for cybersecurity testing, learning, and hands-on practice.

## Table of Contents
1. [Introduction](#introduction)
2. [Lab Setup Overview](#lab-setup-overview)
3. [Step-by-Step Process](#step-by-step-process)
    1. [Set Up pfSense Firewall](#1-set-up-pfsense-firewall)
    2. [Set Up Kali Linux](#2-set-up-kali-linux)
    3. [Set Up Caldera](#3-set-up-caldera)
    4. [Set Up Wazuh](#4-set-up-wazuh)
    5. [Set Up Nessus](#5-set-up-nessus)
    6. [Set Up Security Onion](#6-set-up-security-onion)
    7. [Set Up The Hive and Cortex](#7-set-up-the-hive-and-cortex)
    8. [Set Up Vulnerable Machines](#8-set-up-vulnerable-machines)
    9. [Set Up Active Directory Environment](#9-set-up-active-directory-environment)
    10. [Set Up Docker on Ubuntu](#10-set-up-docker-on-ubuntu)
4. [Skills and Technologies Learned](#skills-and-technologies-learned)
5. [References](#references)

## Introduction

This project aims to create a comprehensive cybersecurity lab for hands-on practice and learning. The lab includes a variety of tools such as firewalls, SIEM, vulnerability scanners, and more.

## Lab Setup Overview

- **Firewall**: pfSense
- **Security Tools**: Kali Linux, Caldera, Wazuh, Nessus, Security Onion, The Hive, Cortex
- **Vulnerable Machines**: Metasploitable 2, BWAPP, DVWA
- **Active Directory**: Windows Server 2022, Windows 10/11 clients
- **Containerization**: Docker on Ubuntu

## Step-by-Step Process

### 1. Set Up pfSense Firewall

1. **Download and Install pfSense**:
    - Download the pfSense ISO from the official website.
    - Install pfSense on a virtual machine or physical hardware.
2. **Configure pfSense**:
    - Set up the WAN and LAN interfaces.
    - Assign IP addresses and configure DHCP.
    - Set up firewall rules to allow traffic between different VLANs.
    - Create VLANs for different network segments.

### 2. Set Up Kali Linux

1. **Download Kali Linux**:
    - Download the Kali Linux ISO from the official website.
2. **Install Kali Linux**:
    - Create a new virtual machine for Kali Linux.
    - Install Kali Linux using the downloaded ISO.
3. **Configure Kali Linux**:
    - Set up network configurations.
    - Install additional tools as needed.

### 3. Set Up Caldera

1. **Clone Caldera Repository**:
    ```sh
    git clone https://github.com/mitre/caldera.git --recursive --branch 4.2.0
    ```
2. **Install Dependencies**:
    - Install Python 3.8 and Pip.
    ```sh
    pip install -r requirements.txt
    ```
3. **Run Caldera**:
    ```sh
    python3 server.py --insecure
    ```

### 4. Set Up Wazuh

1. **Download and Install Wazuh**:
    - Follow the [official Wazuh installation guide](https://documentation.wazuh.com/current/installation-guide/index.html).
2. **Configure Wazuh**:
    - Set up Wazuh manager and agents.
    - Integrate Wazuh with Elastic Stack for visualization.

### 5. Set Up Nessus

1. **Download Nessus**:
    - Download the Nessus installer from the Tenable website.
2. **Install Nessus**:
    - Follow the installation instructions for your operating system.
3. **Configure Nessus**:
    - Set up Nessus with the necessary scanning policies.
    - Run vulnerability scans.

### 6. Set Up Security Onion

1. **Download Security Onion ISO**:
    - Download from the official Security Onion website.
2. **Install Security Onion**:
    - Create a new virtual machine and install Security Onion using the ISO.
3. **Configure Security Onion**:
    - Run through the setup wizard to configure the network settings and sensor configurations.

### 7. Set Up The Hive and Cortex

1. **Create Docker Compose File**:
    - Create a `docker-compose.yml` with the following content:
    ```yaml
    version: '2.1'
    services:
      thehive:
        image: thehiveproject/thehive:latest
        ports:
          - "9000:9000"
        environment:
          - CORTEX_URL=http://cortex:9001
          - CORTEX_KEY=supersecretkey
      cortex:
        image: thehiveproject/cortex:latest
        ports:
          - "9001:9001"
    ```
2. **Deploy Using Docker Compose**:
    ```sh
    docker-compose up -d
    ```

### 8. Set Up Vulnerable Machines

1. **Metasploitable 2**:
    - Download the Metasploitable 2 VM.
    - Import it into your virtualization platform and configure network settings.
2. **BWAPP and DVWA**:
    - Deploy BWAPP and DVWA using Docker containers or install them on a web server.

### 9. Set Up Active Directory Environment

1. **Install Windows Server 2022**:
    - Download the ISO from Microsoft.
    - Create a new VM and install Windows Server 2022.
2. **Configure Active Directory**:
    - Promote the server to a domain controller.
    - Set up DNS and DHCP services.
3. **Join Windows 10/11 Clients to the Domain**:
    - Install Windows 10/11 on VMs.
    - Join these machines to the Active Directory domain.

### 10. Set Up Docker on Ubuntu

1. **Install Docker**:
    ```sh
    sudo apt update
    sudo apt install docker.io
    ```
2. **Install Docker Compose**:
    ```sh
    sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    ```
3. **Deploy Containers**:
    - Create Docker Compose files for various applications and deploy them.

## Skills and Technologies Learned

- **Network Configuration**: VLANs, static IPs, firewall rules.
- **Virtualization**: Setting up VMs using different hypervisors.
- **Linux Administration**: Installing and configuring various Linux-based tools.
- **Windows Server Administration**: Active Directory, DNS, DHCP, Group Policy.
- **SIEM**: Setting up and using Wazuh.
- **Vulnerability Scanning**: Using Nessus.
- **Threat Hunting and Monitoring**: Using Security Onion.
- **Incident Response**: Using The Hive and Cortex.
- **Docker**: Deploying applications using Docker and Docker Compose.

## References

- [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/)
- [Kali Linux Documentation](https://www.kali.org/docs/)
- [Caldera GitHub Repository](https://github.com/mitre/caldera)
- [Wazuh Documentation](https://documentation.wazuh.com/current/index.html)
- [Nessus Documentation](https://docs.tenable.com/nessus/)
- [Security Onion Documentation](https://docs.securityonion.net/en/latest/)
- [The Hive Project Documentation](https://github.com/TheHive-Project/TheHive)
- [Docker Documentation](https://docs.docker.com/)
