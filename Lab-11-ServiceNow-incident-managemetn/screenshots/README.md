# Lab 11 — ServiceNow Incident Management

## Overview

This lab demonstrates hands-on experience with ServiceNow Incident Management in a Personal Developer Instance (PDI).

The objective was to simulate common IT Help Desk and Desktop Support scenarios, practice ITIL-based incident prioritization, document troubleshooting activities, and manage incidents through different stages of their lifecycle.

Three simulated incidents were created to practice incident resolution, escalation, and ticket documentation.

## Technologies & Skills

- ServiceNow Personal Developer Instance (PDI)
- ITIL Incident Management
- Incident Prioritization (Impact and Urgency)
- Incident Lifecycle Management
- Assignment Groups and Escalation
- Internal Work Notes
- Customer-Facing Comments
- Troubleshooting Documentation
- Windows 11 Support
- Microsoft Outlook / Microsoft 365 Support

---

## Incident 1 — Microsoft Outlook Access Issue

**Incident Number:** INC0010002

**Short Description:** User unable to access Outlook email

**Scenario:**

An employee reported being unable to access Microsoft Outlook.

**Simulated Troubleshooting:**

1. Verified network connectivity.
2. Checked access to Outlook on the Web.
3. Investigated the Outlook desktop application's connection status.
4. Identified Work Offline mode as the simulated root cause.
5. Disabled Work Offline mode.
6. Documented restored email synchronization as the simulated outcome.

**Incident Lifecycle:**

New → In Progress → Resolved

**Resolution:**

The simulated issue was resolved by disabling Outlook's Work Offline mode.

### Evidence

![Outlook Incident Resolution](screenshots/INC0010002-outlook-resolution.png)

---

## Incident 2 — Critical Network Outage

**Incident Number:** INC0010003

**Short Description:** Entire department unable to access network

**Scenario:**

Multiple employees in the same department reported losing corporate network connectivity.

The incident was classified as a critical issue due to its significant business impact.

**Incident Classification:**

| Field | Value |
|---|---|
| Impact | 1 - High |
| Urgency | 1 - High |
| Priority | 1 - Critical |
| Assignment Group | Network |

**Actions Performed:**

1. Created a network outage incident.
2. Assessed the business impact and urgency.
3. Assigned the incident a critical priority using ServiceNow's priority calculation.
4. Assigned the ticket to the Network support group.
5. Documented the reason for escalation in internal Work Notes.
6. Identified potential troubleshooting areas, including switch connectivity, VLAN configuration, and DHCP availability.

**Escalation:**

The incident was assigned to the Network support group for further investigation.

No network repair or resolution was performed as part of this simulation.

### Evidence

**Priority Classification**

![Network Incident Priority](screenshots/INC0010003-network-priority.png)

**Network Team Escalation**

![Network Incident Escalation](screenshots/INC0010003-network-escalation.png)

---

## Incident 3 — Windows 11 Printing Issue

**Incident Number:** INC0010004

**Short Description:** User unable to print from Windows 11 workstation

**Scenario:**

A user reported being unable to print from their Windows 11 workstation while other employees could print successfully.

**Incident Classification:**

| Field | Value |
|---|---|
| Impact | 3 - Low |
| Urgency | 3 - Low |
| Priority | 4 - Low |
| Assignment Group | Service Desk |
| State | New |

**Documented Troubleshooting Plan:**

1. Verify printer power and network connectivity.
2. Check the default printer configuration.
3. Inspect the Windows print queue.
4. Verify that the printer is not in Offline mode.
5. Restart the Print Spooler service if necessary.
6. Check printer drivers and perform a test print.
7. Escalate the incident if troubleshooting does not resolve the issue.

**Outcome:**

The incident was created, classified, assigned to the Service Desk group, and documented with a troubleshooting plan.

The troubleshooting steps were documented as part of a simulation and were not executed on a physical printer.

### Evidence

**Incident Priority and Assignment**

![Printer Incident Priority](screenshots/INC0010004-printer-priority.png)

**Internal Troubleshooting Documentation**

![Printer Work Notes](screenshots/INC0010004-printer-worknotes.png)

---

## ITIL Concepts Practiced

### Impact vs. Urgency

**Impact** describes how many users or business services are affected by an incident.

**Urgency** describes how quickly an incident needs to be addressed.

ServiceNow combines these factors using a configurable priority matrix.

### Incident Lifecycle

Practiced transitioning an incident through the following states:

New → In Progress → Resolved

### Escalation

Practiced assigning a critical incident to a specialized Network support group when the issue exceeded the scope of routine Desktop Support.

### Documentation

Practiced the difference between:

- **Customer Comments:** Updates visible to the affected user.
- **Work Notes:** Internal troubleshooting and escalation documentation.

---

## Key Takeaways

This lab provided practical exposure to ServiceNow's incident management interface and common IT Support workflows.

Key skills developed:

- Creating and managing support tickets.
- Determining incident priority based on business impact and urgency.
- Assigning tickets to appropriate support teams.
- Documenting troubleshooting plans and simulated results.
- Recording internal escalation notes.
- Resolving incidents and recording resolution information.
- Understanding the importance of clear communication and accurate ticket documentation.

**Environment:** ServiceNow Personal Developer Instance (PDI)

**Lab Type:** Simulated IT Support / Desktop Support scenarios