# TCP Congestion Control: CUBIC vs. BBR
### Technical Analysis & Executive Communication · Dimitrios Dalaklidis

---

## Overview

This repository contains a consulting-style technical presentation analysing two competing TCP congestion control algorithms — **TCP CUBIC** and **TCP BBR** — across real-world deployment scenarios including LTE mobile networks and cloud file backup systems.

The project demonstrates the ability to take dense, peer-reviewed networking research and distil it into structured, decision-ready communication for both technical and non-technical audiences.

---

## Business Problem

Organisations running large-scale data infrastructure — cloud backup services, CDNs, real-time platforms — routinely face a silent performance problem: **the wrong TCP congestion control algorithm**.

Choosing between CUBIC and BBR is not a purely technical decision. It has measurable impact on:

- **End-user latency** and application responsiveness
- **Bandwidth utilisation** and infrastructure cost
- **Fairness** across concurrent network flows
- **Operational complexity** of network tuning at scale

This analysis provides a framework for understanding those trade-offs and matching protocol choice to use-case requirements.

---

## Key Findings

| Scenario | Recommended Protocol | Rationale |
|---|---|---|
| Cloud file backup over LTE | **TCP BBR** | Lower latency, avoids bufferbloat, adapts to variable bandwidth |
| Small file transfers (~1 MB) | **TCP CUBIC** | BBR's aggressive startup phase inflates RTT for short-lived flows |
| Mixed-protocol environments | **Caution with BBR** | BBR can dominate bandwidth, creating fairness issues alongside CUBIC flows |
| High-bandwidth stable links | **TCP BBR** | Sustained throughput gains without relying on packet loss as a signal |

> **Core insight:** There is no universally superior protocol. The right choice depends on network topology, traffic profile, and performance priorities. This is a decision framework, not a binary recommendation.

---

## What This Project Demonstrates

### Technical Depth
- Understanding of TCP internals: congestion windows, RTT estimation, AIMD, SACK, RTO sensitivity
- Analysis of loss-based vs. model-based congestion control paradigms
- Application of academic research (Li et al., PAM 2017; RFC 793; RFC 2018) to practical infrastructure decisions

### Consulting & Communication Skills
- Translation of complex protocol behaviour into business-relevant trade-off analysis
- Structured argumentation: problem framing → mechanism → evidence → recommendation
- Visual communication of technical comparisons for mixed audiences
- Citation of primary sources with clear attribution

### Analytical Framework Applied
1. **Problem definition** — Why does TCP need congestion control, and what are the costs of getting it wrong?
2. **Mechanism comparison** — How do CUBIC and BBR differ in their approach to estimating network capacity?
3. **Evidence-based evaluation** — What does empirical research show about performance across scenarios?
4. **Contextual recommendation** — Which protocol is appropriate under which conditions, and why?

---

## Presentation Structure

| Slide | Content |
|---|---|
| 1 | Title & framing |
| 2 | The core problem: TCP's blind estimation problem & two competing approaches |
| 3 | Real-world trade-offs: throughput, small transfers, fairness — with verdicts |

Designed to be readable by a network engineer and a product manager simultaneously.

---

## Source Material

| Reference | Description |
|---|---|
| Li et al., PAM 2017 | *TCP CUBIC versus BBR on the Highway* — primary empirical source |
| RFC 793 (Postel, 1981) | Original TCP specification |
| RFC 2018 (Mathis et al., 1996) | TCP Selective Acknowledgment (SACK) |
| Muthitacharoen et al., SOSP 2001 | Low-bandwidth network file systems |
| Ghemawat et al., SOSP 2003 | Google File System — cloud storage context |
| Le Boudec & Thiran, 2001 | Network Calculus — queuing theory foundations |

---

## About

**Dimitrios Dalaklidis**  
B.Sc. Computer Science — University of Western Macedonia (Expected July 2026)  
C2 English Proficiency (ECPE)

This project sits at the intersection of systems programming and technical communication, reflecting an interest in roles where engineering knowledge informs business decisions, not just implementation.

[LinkedIn](https://linkedin.com/in/dimitris-dalaklidis) · [GitHub](https://github.com/DimitriosDalaklidhs) · dalaklidesdemetres@gmail.com
