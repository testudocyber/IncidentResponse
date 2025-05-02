# 1.01 – Troop Leading Procedures (TLP) for Cyber Incident Response

## Purpose

This document adapts the military Troop Leading Procedures (TLP) framework to guide incident response (IR) teams in planning and executing cybersecurity operations. It provides a structured approach to rapidly assess, plan, and respond to cyber incidents, ensuring coordinated and effective action.

## Standards

The TLP framework consists of eight steps:

1. **Receive the Mission**
2. **Issue a Warning Order (WARNORD)**
3. **Make a Tentative Plan**
4. **Initiate Movement**
5. **Conduct Reconnaissance**
6. **Complete the Plan**
7. **Issue the Complete Order**
8. **Supervise and Refine**

> **Note:** These steps are iterative and may overlap depending on the situation and time constraints.

## End State

The goal is to enable incident response teams to:

- Rapidly assess and understand the incident.
- Develop and communicate a clear response plan.
- Coordinate actions across all involved parties.
- Effectively contain, eradicate, and recover from the incident.
- Continuously improve response capabilities through supervision and refinement.

---

# Procedural Steps

<details>
<summary><strong>1. Receive the Mission</strong></summary>

**Objective:** Understand the nature and scope of the incident.

**Actions:**

- Gather initial information from alerts, reports, or notifications.
- Identify affected systems, data, and stakeholders.
- Determine the incident classification and severity.
- Assign an incident commander or lead responder.

**Tools:**

- SIEM systems (e.g., Splunk, ELK Stack).
- Incident tracking systems (e.g., Jira, ServiceNow).

</details>

<details>
<summary><strong>2. Issue a Warning Order (WARNORD)</strong></summary>

**Objective:** Alert relevant parties to prepare for potential response actions.

**Actions:**

- Disseminate initial incident information.
- Provide preliminary guidance on potential actions and resource mobilization.
- Establish communication channels for ongoing coordination.

**Tools:**

- Email, messaging platforms (e.g., Slack, Microsoft Teams).
- Emergency notification systems.

</details>

<details>
<summary><strong>3. Make a Tentative Plan</strong></summary>

**Objective:** Develop an initial response strategy.

**Actions:**

- Analyze the incident using frameworks like MITRE ATT&CK.
- Identify potential containment, eradication, and recovery steps.
- Assess resource requirements and constraints.
- Coordinate with legal, compliance, and public relations teams.

**Tools:**

- Threat intelligence platforms.
- Network and system analysis tools (e.g., Wireshark, Nmap).

</details>

<details>
<summary><strong>4. Initiate Movement</strong></summary>

**Objective:** Begin mobilizing resources and taking preparatory actions.

**Actions:**

- Deploy incident response team members to critical locations or systems.
- Isolate affected systems to prevent further compromise.
- Begin collecting forensic data for analysis.

**Tools:**

- Endpoint detection and response (EDR) tools (e.g., CrowdStrike, Carbon Black).
- Forensic imaging tools (e.g., FTK Imager, EnCase).

</details>

<details>
<summary><strong>5. Conduct Reconnaissance</strong></summary>

**Objective:** Gather detailed information to inform the final response plan.

**Actions:**

- Perform in-depth analysis of affected systems and networks.
- Identify indicators of compromise (IOCs) and attack vectors.
- Assess the extent of data exfiltration or system damage.

**Tools:**

- Log analysis tools (e.g., LogRhythm, Graylog).
- Malware analysis sandboxes (e.g., Cuckoo Sandbox).

</details>

<details>
<summary><strong>6. Complete the Plan</strong></summary>

**Objective:** Finalize the response strategy with detailed actions and assignments.

**Actions:**

- Develop a comprehensive incident response plan (IRP) document.
- Assign specific tasks to team members with clear timelines.
- Coordinate with external partners or vendors as necessary.

**Tools:**

- Project management tools (e.g., Trello, Asana).
- Documentation platforms (e.g., Confluence, SharePoint).

</details>

<details>
<summary><strong>7. Issue the Complete Order</strong></summary>

**Objective:** Communicate the finalized plan to all stakeholders for execution.

**Actions:**

- Distribute the IRP to all relevant parties.
- Conduct briefings to ensure understanding of roles and responsibilities.
- Establish checkpoints for progress updates and adjustments.

**Tools:**

- Video conferencing tools (e.g., Zoom, Webex).
- Shared calendars and scheduling tools.

</details>

<details>
<summary><strong>8. Supervise and Refine</strong></summary>

**Objective:** Oversee the execution of the response plan and make necessary adjustments.

**Actions:**

- Monitor the progress of response activities.
- Address any obstacles or unforeseen developments.
- Conduct after-action reviews to identify lessons learned.
- Update incident response procedures and documentation accordingly.

**Tools:**

- Performance monitoring tools.
- Feedback collection platforms (e.g., surveys, debrief forms).

</details>

---

## Tools and Resources

| Category | Tools |
|----------|-------|
| SIEM Systems | Splunk, ELK Stack |
| EDR Tools | CrowdStrike, Carbon Black |
| Forensic Tools | FTK Imager, EnCase |
| Communication Platforms | Slack, Microsoft Teams, Zoom |
| Project Management | Trello, Asana, Confluence |

---

## References

- CALL Handbook 15-06: Military Decision Making Process (MDMP)
- 150-LDR-5012: Conduct Troop Leading Procedures
- ADP 6-22: Army Leadership
- NIST SP 800-61 Rev. 2: Computer Security Incident Handling Guide
- MITRE ATT&CK Framework: Adversarial Tactics, Techniques, and Common Knowledge
