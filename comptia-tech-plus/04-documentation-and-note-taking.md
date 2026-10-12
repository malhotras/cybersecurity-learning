# 04 - Documentation and Note-Taking in IT and Cybersecurity

## 1. What Is Technical Documentation?

Technical documentation records information about computer systems, configurations, procedures, problems, and solutions.

In IT and cybersecurity, documentation helps teams:
- Understand how systems work.
- Troubleshoot technical problems.
- Communicate findings between team members.
- Record security incidents and response actions.
- Maintain accountability and support audits.
- Learn from previous problems and prevent recurrence.

Good documentation should be accurate, clear, organized, objective, and easy to follow.

## 2. Types of Technical Documentation

| Document Type | Purpose |
|---|---|
| System documentation | Describes system architecture, hardware, software, and configuration |
| Network documentation | Records network diagrams, devices, addresses, and connections |
| User documentation | Explains how to use a system or application |
| Troubleshooting guide | Provides steps for diagnosing and resolving problems |
| Change record | Documents system changes, approvals, and outcomes |
| Incident report | Records a security incident and the response |
| Penetration test report | Documents authorized security testing and its findings |
| Standard operating procedure (SOP) | Describes a repeatable process step by step |

## 3. Good Note-Taking Practices

Effective technical notes answer these questions:

- What happened?
- When did it happen?
- Which system or user was affected?
- What evidence was observed?
- What actions were taken?
- What was the result?
- What should happen next?

### Example: Troubleshooting Note

**Problem:** A workstation cannot access a shared folder.

**Time:** 10:15

**System:** WORKSTATION-04

**Observations:**
- The user can access the internet.
- The shared folder is unavailable.
- The error message indicates an access problem.

**Actions:**
1. Confirmed the folder path.
2. Checked network connectivity.
3. Reviewed the user's group membership and permissions.
4. Tested access after the approved permission correction.

**Outcome:** Access restored.

**Follow-up:** Review the access configuration and document the approved change.

This is an illustrative example, not a real incident record.

## 4. Penetration Testing Reports

A penetration test is an authorized assessment that attempts to identify and validate security weaknesses.

A penetration testing report communicates the results to technical teams and management.

### Typical Report Sections

1. Executive summary
2. Scope and objectives
3. Testing methodology
4. Findings and evidence
5. Risk ratings
6. Business impact
7. Remediation recommendations
8. Conclusion

### Example Finding

**Finding:** A test account has excessive permissions on a shared folder.

**Risk:** Users may be able to access information beyond their job requirements.

**Evidence:** Approved testing confirms that the account can read files outside its intended access scope.

**Recommendation:** Review group membership, correct permissions, and retest access.

Testing must remain within the agreed authorization and scope.

## 5. Incident Response Documentation

A security incident is an event that compromises or threatens the confidentiality, integrity, or availability of systems or information.

An incident report records what happened and how the organization responded.

### Important Information to Record

- Incident identifier and severity
- Date and time of detection
- Affected systems and accounts
- Detection source, such as an alert or user report
- Relevant logs and other evidence
- Investigation findings
- Containment and recovery actions
- Communications and escalations
- Final outcome and lessons learned

### Common Incident Response Stages

1. Preparation
2. Detection and analysis
3. Containment
4. Eradication
5. Recovery
6. Lessons learned and improvement

Organizations may use different frameworks, and actual response activities can overlap.

## 6. Evidence Handling

Evidence helps investigators support conclusions about an incident.

Examples include:
- Authentication logs
- Firewall logs
- Endpoint security alerts
- System timestamps
- Relevant screenshots
- Forensic copies of storage or memory
- File hashes

### Evidence Handling Principles

- Record where and when evidence was collected.
- Identify the person or process that collected it.
- Preserve original evidence where possible.
- Restrict access to authorized personnel.
- Record transfers and access.
- Use approved collection and storage procedures.
- Document relevant timestamps and time zones.

### Chain of Custody

The chain of custody is a record of who collected, handled, transferred, or stored evidence and when those actions occurred.

A clear chain of custody helps establish that evidence was handled appropriately and supports its credibility.

## 7. Timestamps and Incident Timelines

A timeline organizes important events in chronological order.

Example:

| Time (UTC) | Event |
|---|---|
| 09:00 | Suspicious login alert generated |
| 09:05 | Analyst begins investigation |
| 09:12 | Account temporarily disabled |
| 09:25 | Relevant authentication logs preserved |
| 10:00 | Investigation expanded to related systems |

This is a fictional example.

Record the time zone and use consistent timestamps. This is particularly important when evidence comes from systems in different locations.

## 8. The Equifax Data Breach Case Study

Equifax experienced a major data breach in 2017 that exposed sensitive personal information.

The incident is an important case study in vulnerability management, security monitoring, incident response, and accountability.

### High-Level Summary

- A vulnerability affecting Apache Struts had a security patch available before the breach.
- Attackers exploited the weakness in Equifax's systems.
- The breach affected the personal information of approximately 147 million people in the United States.
- Equifax announced the breach publicly in September 2017.
- Government investigations examined the security failures and the organization's response.

### Why Documentation Matters in This Case

Incident records and investigation reports help establish:
- Which vulnerability was involved.
- Which systems were affected.
- When suspicious activity occurred and was detected.
- What information was exposed.
- Which response actions were taken.
- Which security improvements were needed.

### Lessons Learned

- Maintain an accurate inventory of systems and software.
- Apply security patches promptly.
- Monitor systems for suspicious activity.
- Preserve relevant logs and evidence.
- Record incident decisions and response actions.
- Review the incident afterward and improve security controls.

### Further Reading

- [U.S. Government Accountability Office: Equifax Data Breach](https://www.gao.gov/products/gao-18-559)
- [U.S. Federal Trade Commission: Equifax Data Breach Settlement](https://www.ftc.gov/enforcement/refunds/equifax-data-breach-settlement)

## 9. Writing Clear Technical Notes

Use these guidelines when documenting technical work:

- Be specific rather than vague.
- Separate observed facts from assumptions.
- Include relevant error messages.
- Record commands and their results when appropriate.
- Use dates, times, and time zones consistently.
- Avoid including passwords, access tokens, or unnecessary personal information.
- Explain what was changed and how the result was verified.
- Write for the intended audience.

Weak note:
"Fixed the network."

Better note:
"Restored access to the shared folder after confirming the network connection and correcting the user's approved folder permissions. Verified access with the affected account."

## 10. Practice Questions

### Question 1
What is the primary purpose of a penetration testing report?

A. Replace all security controls  
B. Document authorized testing, findings, evidence, and recommendations  
C. Store user passwords  
D. Guarantee that a system cannot be attacked  

### Question 2
What does chain of custody record?

A. Computer performance only  
B. The handling and transfer of evidence  
C. The list of installed applications  
D. Network bandwidth  

### Question 3
Why should an incident timeline use consistent timestamps and time zones?

A. To make the report longer  
B. To help establish the sequence of events accurately  
C. To remove the need for evidence  
D. To avoid documenting response actions  

### Question 4
Which item is most useful in an incident report?

A. Unsupported assumptions  
B. Relevant logs and recorded response actions  
C. Unrelated personal opinions  
D. Unverified rumors  

### Question 5
What is the purpose of lessons learned after an incident?

A. Identify improvements that may prevent similar incidents  
B. Delete all security logs  
C. Avoid reviewing the incident  
D. Eliminate the need for patching  

### Question 6
Which is the best example of clear technical documentation?

A. "Computer broken."
B. "Something went wrong."
C. "The application returned error 403 at 14:20 UTC; access permissions were reviewed and the result was recorded."
D. "The issue was probably a hacker."

### Question 7
Why should evidence access be restricted?

A. To prevent investigators from documenting anything  
B. To protect evidence from unauthorized access or alteration  
C. To guarantee that every incident is solved  
D. To avoid creating a timeline  

### Question 8
What was a major lesson from the Equifax breach?

A. Security patches are unnecessary  
B. Vulnerability management and timely patching are important  
C. Documentation prevents every cyberattack  
D. Network monitoring should always be disabled  

## Answers and Explanations

1. B - A penetration test report records findings, evidence, risk, and remediation.
2. B - Chain of custody tracks the handling and transfer of evidence.
3. B - Consistent timestamps help investigators reconstruct events.
4. B - Relevant evidence and actions support reliable conclusions.
5. A - Lessons learned identify improvements to security and response.
6. C - It includes a specific error, timestamp, and documented action.
7. B - Restricting access helps protect evidence integrity and confidentiality.
8. B - Timely patching and effective vulnerability management are essential.

## Revision Checklist

- [ ] Explain why technical documentation matters.
- [ ] Identify the sections of a penetration test report.
- [ ] Explain the purpose of an incident response report.
- [ ] Define evidence and chain of custody.
- [ ] Explain the purpose of an incident timeline.
- [ ] Distinguish facts from assumptions.
- [ ] Describe the high-level lessons from the Equifax breach.
- [ ] Write a clear troubleshooting note.

## Further Reading

- [CompTIA Tech+](https://www.comptia.org/certifications/tech)
- [NIST Computer Security Incident Handling Guide](https://csrc.nist.gov/pubs/sp/800/61/r2/final)
- [U.S. GAO Equifax Report](https://www.gao.gov/products/gao-18-559)
