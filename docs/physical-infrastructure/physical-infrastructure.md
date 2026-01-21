# Physical Infrastructure Deployment Overview  
**Network Deployment · Meraki Architecture · Site Provisioning · Connectivity Governance**

This document summarizes the physical infrastructure deployed across multiple office locations as part of an initial expansion project.  
The objective was to deliver secure, functional, and supportable network environments under tight timelines and with minimal on-site resources.

This represents current-state implementation and excludes future-state enhancements unless stated.

---

## 1. Scope & Objectives

The deployment included new office locations requiring:

- Complete network stack installation  
- Secure connectivity back to the primary hub  
- Workstation, phone, printer, and camera provisioning  
- Baseline governance and documentation  

Goals:

- Establish stable, secure, centrally managed infrastructure  
- Standardize deployment across all sites  
- Enable site-to-site communication using AutoVPN  
- Prepare each site for future expansion (cameras, segmentation, backups)

---

## 2. Sites Deployed

Three office locations were included in this phase:

- **Newark, DE**  
- **Seaford, DE**  
- **Milford, DE**

Each site received an identical architectural pattern for consistency and operational simplicity.

---

## 3. Network Architecture & Controls

All sites were built using a standardized Meraki-centric architecture:

### 3.1 Core Components
- ISP gateway handoff  
- Meraki MX75 (routing, security, AutoVPN authority)  
- Business-class unmanaged PoE switches  
- Meraki 150AX wireless access point  
- UPS units for power stability  

### 3.2 Design Principles
- Meraki MX as the **authoritative routing and security boundary**  
- Centralized NAT, DHCP, and LAN services  
- Consistent private subnet allocation per site (`172.31.x.0/24`)  
- AutoVPN hub-and-spoke topology back to primary location  
- Verizon gateway radios disabled to avoid wireless overlap  
- UPnP disabled across ISP gateways  

### 3.3 Governance Controls
- All Meraki devices claimed and assigned to correct networks  
- DHCP reservations for MX appliances  
- Single-pane-of-glass visibility through Meraki Dashboard  
- ISP-managed equipment documented for support escalation  

This ensures stable remote management and clear ownership boundaries.

---

## 4. Hardware Deployment (Per Site)

The following equipment was deployed and validated:

- **1× Meraki MX75** (routing, firewall, VPN)  
- **1× Meraki 150AX AP** (Wi-Fi)  
- **2× PoE business switches**  
- **3× Windows 11 Pro workstations**  
- **1× Printer (networked)**  
- **1× Document scanner**  
- **2× IP phones**  
- **1× IP camera** (powered and reset; storage not available yet)  
- **UPS battery backup units**

Each workstation was:

- Upgraded to Windows 11 Pro  
- Onboarded to Intune via Autopilot  
- Enrolled in Defender  
- Configured with site-standard naming  
- Validated for connectivity, printing, and VOIP

---

## 5. Deployment Status Summary

### **Newark, DE**
- Full network deployment complete  
- AutoVPN operational  
- Wireless and LAN validated  
- Endpoints deployed and tested  
- Cameras powered/reset; configuration deferred  

### **Seaford, DE & Milford, DE**
- Network deployment complete  
- AutoVPN operational  
- Partial endpoint deployment  
- Camera configuration deferred due to missing storage system  

### Documented constraints:
- No NVR/NAS storage available  
- Camera retention policies pending  
- Camera VLAN segmentation deferred  
- Physical camera mounting not included in scope  

---

## 6. Governance & Ownership

- **Infrastructure Owner:** Organization  
- **Deployment & Configuration Owner:** System Engineer  
- **Network Platform:** Cisco Meraki Dashboard  
- **ISP Platform:** Verizon Business Gateway  

Licensing and device provisioning were validated via official vendor portals.

---

## 7. Deferred Items (Future Phase)

The following items will be addressed later:

- NVR/NAS deployment for camera storage  
- Camera VLAN segmentation (if required)  
- Centralized camera management  
- Backup/DR strategy for each Delaware location  
- Additional AP provisioning pending capacity analysis  

These items are tracked as part of post-deployment planning.

---

## 8. Network Topology Documentation

Topology diagrams are maintained outside this repository to avoid version drift.  
Authoritative diagrams include:

- ISP demarcation  
- Routing and firewall boundaries  
- AutoVPN relationships  
- Switch stack layout  
- AP placement and coverage  

Documents updated under change-controlled workflow.

---

## 9. Document Intent

This document provides a concise overview of the physical network architecture and deployment activities completed during the Delaware expansion project.  
It demonstrates hands-on infrastructure capability aligned with modern cloud and security architecture.
