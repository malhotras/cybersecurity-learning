# Threat Modelling and Incident Response

## Threat Modelling

**Threat modelling** is the process of identifying, evaluating, and addressing potential threats and vulnerabilities in an organisation's systems and applications.

The main goals are to:

- Identify potential threats
- Identify vulnerabilities
- Assess risk
- Develop appropriate mitigations
- Review and improve security controls

An effective threat model can include:

- Threat intelligence
- Asset identification
- Risk assessment
- Mitigation capabilities

---

## STRIDE

**STRIDE** is a threat-modelling framework containing six categories of threats:

| Principle | Description |
|---|---|
| **Spoofing** | Pretending to be another user or identity |
| **Tampering** | Illegally modifying data or information |
| **Repudiation** | Preventing reliable tracking of actions, often addressed with logging |
| **Information Disclosure** | Exposing information to unauthorised users |
| **Denial of Service** | Making a system or service unavailable |
| **Elevation of Privilege** | Gaining higher permissions than authorised |

### Easy way to remember

**S** — Spoofing  
**T** — Tampering  
**R** — Repudiation  
**I** — Information Disclosure  
**D** — Denial of Service  
**E** — Elevation of Privilege

---

## Incident Response

A security breach is known as an **incident**. The process of responding to and recovering from a security incident is called **Incident Response (IR)**.

A **Computer Security Incident Response Team (CSIRT)** is a group responsible for responding to security incidents.

### Six Phases of Incident Response

| Phase | Purpose |
|---|---|
| **Preparation** | Make sure resources and plans are available |
| **Identification** | Identify the threat and threat actor |
| **Containment** | Prevent the incident from spreading |
| **Eradication** | Remove the active threat |
| **Recovery** | Return affected systems to normal operation |
| **Lessons Learned** | Review the incident and improve future security |

---

## Questions

### Q1. What model outlines "Spoofing"?

**Answer:** `STRIDE`

Spoofing is one of the six categories in the STRIDE threat-modelling framework.

### Q2. What does the acronym "IR" stand for?

**Answer:** `Incident Response`

Incident Response is the process of responding to and recovering from security incidents.

### Q3. You are tasked with adding some measures to an application to improve the integrity of data. What STRIDE principle is this?

**Answer:** `Tampering`

Tampering involves the unauthorised modification of data. Measures that protect data integrity help prevent tampering.

### Q4. An attacker has penetrated your organisation's security and stolen data. It is your task to return the organisation to business as usual. What incident response stage is this?

**Answer:** `Recovery`

Recovery involves restoring affected systems and returning the organisation to normal operations.

---

## Key Takeaway

**Threat modelling → identify threats and vulnerabilities before they cause incidents.**

**STRIDE → a framework for categorising common threats.**

**Incident Response → prepare, identify, contain, eradicate, recover, and learn.**
