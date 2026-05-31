# osTicket — Ticket Lifecycle (Intake to Resolution)

![osTicket logo](https://i.imgur.com/Clzj7Xs.png)

This project demonstrates the full lifecycle of a support ticket in osTicket — from the moment an end user submits a request, all the way through triage, communication, prioritization, and final resolution. This is Part 3 of a three-part osTicket series.

> **Prerequisite:** This project builds on the configuration completed in Part 2: [osTicket — Post-Install Configuration](https://github.com/solomonyohanis/osticket-post-install-config)

---

## Environments and Technologies Used

- Windows 11 (Virtual Machine)
- Internet Information Services (IIS)
- osTicket v1.18
- Microsoft Edge (Browser)

---

## osTicket Portal URLs

| Portal | URL | Purpose |
|---|---|---|
| **End User Portal** | `http://localhost/osTicket/` | Public-facing help desk — end users submit and track tickets here |
| **Admin / Agent Login** | `http://localhost/osTicket/scp/login.php` | Staff portal — agents and admins log in here to manage and resolve tickets |

---

## Ticket Lifecycle Steps

1. [End User Submits a Ticket](#step-1--end-user-submits-a-ticket)
2. [Ticket Confirmation](#step-2--ticket-confirmation)
3. [Agent Views the Ticket Queue](#step-3--agent-views-the-ticket-queue)
4. [Agent Opens and Reviews the Ticket](#step-4--agent-opens-and-reviews-the-ticket)
5. [Agent Posts an Initial Reply](#step-5--agent-posts-an-initial-reply)
6. [Agent Updates the SLA Plan](#step-6--agent-updates-the-sla-plan)
7. [Agent Updates the Priority Level](#step-7--agent-updates-the-priority-level)
8. [Agent Posts a Resolution Reply](#step-8--agent-posts-a-resolution-reply)
9. [Agent Closes the Ticket](#step-9--agent-closes-the-ticket)
10. [Ticket Confirmed Closed](#step-10--ticket-confirmed-closed)

---

## Step 1 — End User Submits a Ticket

**End User Portal → Open a New Ticket**

This is the public-facing side of osTicket, accessible at `http://localhost/osTicket/`. It's where employees or customers go to report issues — no agent login is required. Think of it like the front desk of an IT help desk where anyone can walk up and file a request.

<img width="1920" height="955" alt="01_support_center_home" src="https://github.com/user-attachments/assets/6eb39203-5432-4589-bde7-a23e1eb74d54" />

Navigate to the end user portal. The **Support Center** home page displays two main actions: **Open a New Ticket** (blue button) and **Check Ticket Status** (green button). Click **Open a New Ticket** to begin.

<img width="1920" height="955" alt="02_open_new_ticket_form_empty" src="https://github.com/user-attachments/assets/f86808e7-43e9-4257-9e80-2a62d6edfb48" />

The **Open a New Ticket** form appears. The form requires:
- **Email Address** — used to send updates and confirmation to the user
- **Full Name** — identifies who submitted the ticket
- **Help Topic** — categorizes the type of issue (e.g., "Report a Problem", "General Inquiry")

Help Topics are pre-configured categories that help route tickets to the correct department automatically. They were set up during the post-install configuration phase. For example, selecting "Report a Problem" can automatically route the ticket to the Maintenance or IT department.

<img width="1920" height="955" alt="04_ticket_form_filled_complete" src="https://github.com/user-attachments/assets/a5c626a4-01ad-4f5e-9c5a-ce8cad65acda" />

The end user **Karen** fills in her information:
- **Email:** karen@gmail.com
- **Full Name:** Karen
- **Help Topic:** Report a Problem
- **Issue Summary:** Having an issue visiting the work website
- **Details:** All other employees are not able to reach the work website

The Issue Summary acts as the subject line of the ticket, and the body text provides more detail — similar to writing an email. Once all fields are complete, Karen clicks **Create Ticket**.

---

## Step 2 — Ticket Confirmation

<img width="1920" height="955" alt="05_ticket_created_confirmation" src="https://github.com/user-attachments/assets/acecb9f4-3c11-4f6f-bffe-f01ce11a1c4a" />

After clicking **Create Ticket**, osTicket displays a green confirmation banner: **"Support ticket request created."** Karen is notified that a representative will follow up with her. Behind the scenes, the ticket is now sitting in the agent queue waiting to be picked up.

---

## Step 3 — Agent Views the Ticket Queue

**Agent Panel → Tickets → Open**

This is the staff-facing side of osTicket, accessed at `http://localhost/osTicket/scp/login.php`. Agents (help desk staff) log in here to see incoming tickets, respond to users, and manage resolutions. Only authorized agents can access this area.

<img width="1920" height="955" alt="06_agent_ticket_queue_karen_ticket" src="https://github.com/user-attachments/assets/9a272882-e8c1-4ed4-bf0d-d4f0f3ff32b3" />

After logging in as **Solomon Yohanis** (the agent), the **Open Tickets** queue is visible. Two tickets are listed:
- **#306227** — "osTicket Installed!" (a default welcome ticket from the osTicket Team)
- **#632319** — "Having an issue visiting the work website" — submitted by Karen, with a Priority of **Normal** and currently unassigned

When a ticket first comes in, it may not yet be assigned to any specific agent. A queue manager or the agent themselves can pick it up. The Priority column shows "Normal" by default — this will be updated once the agent reviews the issue.

---

## Step 4 — Agent Opens and Reviews the Ticket

<img width="1920" height="955" alt="07_ticket_632319_post_reply_tab_empty" src="https://github.com/user-attachments/assets/7d9d220b-d036-4a7d-8b0f-a5c5f0007b93" />

The agent clicks on ticket **#632319** to open it. The ticket view shows:
- Karen's original message: *"All other employees are not able to reach the work website"*
- The **Post Reply** tab at the bottom, where the agent can respond directly to Karen
- A **Post Internal Note** tab, used for notes visible only to staff (not sent to the user)

Internal notes are private comments agents leave for each other within a ticket. For example, an agent might note "I escalated this to the networking team" without that message being emailed to the end user. It keeps internal communication organized within the ticket thread.

---

## Step 5 — Agent Posts an Initial Reply

<img width="1920" height="955" alt="08_ticket_reply_drafted" src="https://github.com/user-attachments/assets/f3f28263-6c27-40e8-b79d-7be6a8a7f8ed" />

The agent drafts a reply to Karen acknowledging the issue and communicating the next step. The reply reads:

*"Hi Karen, I see you are not able to reach the work website, I have an idea of what might be the issue, I'm heading over there to take a look."*

The **Ticket Status** at the bottom is left as **Open (current)** since the issue hasn't been resolved yet. The agent clicks **Post Reply** to send the message.

<img width="1920" height="955" alt="09_ticket_thread_after_first_reply" src="https://github.com/user-attachments/assets/6184da97-7fef-43ff-ac6d-2598b1f1749b" />

After posting, the **Ticket Thread** updates to show both Karen's original message and Solomon's reply. The ticket metadata at the top also now reflects:
- **Assigned To:** Solomon Yohanis
- **SLA Plan:** Default SLA
- **Due Date:** 6/3/26 8:00 AM

The ticket thread is the full conversation history of a ticket — every reply, note, and system change is recorded here in chronological order. It ensures anyone picking up the ticket can see exactly what has happened so far.

<img width="1920" height="955" alt="10_ticket_detail_view_sla_update_button" src="https://github.com/user-attachments/assets/2da62164-4185-49f9-9d91-613c10b7c6f9" />

With the full ticket detail view visible, the agent notices the SLA Plan is currently set to **Default SLA**. Since all employees are impacted and cannot access the company website, this is clearly a business-impacting issue that warrants a more urgent SLA. The agent clicks on the **SLA Plan** field to update it.

---

## Step 6 — Agent Updates the SLA Plan

 SLA stands for **Service Level Agreement**. In osTicket, SLA Plans define how quickly a ticket must be responded to or resolved. For example:
 - **Default SLA** — a general fallback plan (18 hours active)
 - **Sev-A** — the most critical; typically 1 hour active, 24/7
 - **Sev-B** — business hours urgency; typically 4 hours active
 - **Sev-C** — lower priority; typically 8 hours active

 Setting the correct SLA ensures the right 
ticket gets attention in the right timeframe. Failing to set an appropriate SLA can cause critical issues to be treated as low priority.

<img width="1920" height="955" alt="11_update_sla_dropdown_sevb_selected" src="https://github.com/user-attachments/assets/5ec159a4-8fd6-4d33-8ef4-2fd380c6e67c" />

The **Update SLA Plan** modal opens with a dropdown showing available options: Default SLA, Sev-A, Sev-B, and Sev-C. The agent selects **Sev-B**.

<img width="1920" height="955" alt="12_update_sla_business_impacting_note" src="https://github.com/user-attachments/assets/a488d100-2c3b-4187-b35c-0e3305464168" />

After selecting Sev-B, the agent enters a reason for the change in the notes field: **"Business impacting."** This note is logged in the ticket thread for audit purposes. The agent clicks **Update**.

<img width="1920" height="955" alt="13_sla_updated_success_sevb_confirmed" src="https://github.com/user-attachments/assets/f74a231d-743c-4b20-a9a4-c6c89c32a023" />

A green confirmation banner appears: **"SLA Plan updated successfully."** The ticket detail now shows:
- **SLA Plan:** Sev-B
- **Due Date:** 6/3/26 8:00 AM (adjusted to the 4-hour active window)

---

## Step 7 — Agent Updates the Priority Level

Priority determines how urgently a ticket should be handled relative to other tickets in the queue. osTicket supports four levels:
 - **Low** — minor inconvenience, no time pressure
 - **Normal** — standard request (the default for new tickets)
 - **High** — significant impact on a user or group
 - **Emergency** — critical system failure affecting the entire organization

 Updating priority helps the queue manager and other agents quickly triage and sort incoming work.

<img width="1920" height="955" alt="14_update_priority_dropdown_high_selected" src="https://github.com/user-attachments/assets/9a7d1bd4-6dd8-4c42-9e09-481e8752759c" />

The agent clicks on the **Priority** field to open the **Update Priority Level** modal. The current priority is **Normal**. The agent selects **High** from the dropdown, since all employees are affected.

<img width="1920" height="955" alt="15_update_priority_high_business_impacting_note" src="https://github.com/user-attachments/assets/6b78b86f-258a-4540-8487-7d865a3444c8" />

The agent enters **"Business impacting"** as the reason for the priority change and clicks **Update**.

<img width="1920" height="955" alt="16_priority_updated_success_high_confirmed" src="https://github.com/user-attachments/assets/cdf15be4-6111-48bc-a7cd-00756bbf6bc6" />

A second green confirmation banner appears: **"Priority Level updated successfully."** The ticket now shows:
- **Priority:** High
- **SLA Plan:** Sev-B

Both changes are recorded as system entries in the ticket thread.

---

## Step 8 — Agent Posts a Resolution Reply

<img width="1920" height="955" alt="17_ticket_thread_audit_trail" src="https://github.com/user-attachments/assets/a047566a-9325-410a-8b06-f81acd740abb" />

Scrolling through the ticket thread, the full audit trail is visible:
- Karen's original report
- Solomon's initial reply
- A system note: **SLA changed from Default SLA (18 hours - Active) to Sev-B (4 hours - Active)**
- A system note: **Priority Level changed from Normal to High**

This audit trail is automatically maintained by osTicket — every action taken on a ticket is logged with a timestamp and the name of the agent who made the change.

<img width="1920" height="955" alt="18_resolution_reply_drafted" src="https://github.com/user-attachments/assets/cfbe6bed-c805-4334-ad8a-f9e76ffe515e" />

After investigating the issue, the agent discovers the root cause and drafts a resolution reply:

*"Hi Karen, Looks like I needed to do a small update on your computer. Please try visiting the work website again."*

The agent clicks **Post Reply** to notify Karen that the issue has been addressed.

<img width="1920" height="955" alt="19_ticket_thread_resolution_reply_posted" src="https://github.com/user-attachments/assets/5b337747-87db-4b55-b8a3-adf6625acce4" />

The thread updates with the new reply from Solomon at 1:52 AM. The conversation now has 5 total entries in the Ticket Thread.

---

## Step 9 — Agent Closes the Ticket

<img width="1920" height="955" alt="20_ticket_status_dropdown_closed_selected" src="https://github.com/user-attachments/assets/070660d0-dd52-46da-beb0-49702214e316" />

With the issue resolved, the agent is ready to close the ticket. Clicking the **flag/status** button in the top-right of the ticket reveals two options: **Resolved** and **Closed**. The agent selects **Closed**.

In osTicket, "Resolved" can mean the fix has been applied but the ticket is still technically open (awaiting confirmation from the user). "Closed" means the ticket is fully completed. For this workflow, the agent closes the ticket directly.

<img width="1920" height="955" alt="21_close_ticket_modal_empty" src="https://github.com/user-attachments/assets/3afb394d-d8df-4962-af95-4a2f5afc325b" />

The **Close Ticket #632319** modal appears with a **Status** set to **Closed** and an optional internal note field for documenting the resolution details.

<img width="1920" height="955" alt="22_close_ticket_modal_resolution_note" src="https://github.com/user-attachments/assets/ea2bfb7d-04ee-4fd9-a532-2a5fb84991a2" />

The agent types a root cause summary in the note field:
- *"Client host still had old Private IP address for webserver."*
- *"Needed to have a simple DNS flush."*

> DNS (Domain Name System) translates domain names like "company.com" into IP addresses that computers use to connect. When a server moves to a new IP address, client machines may still have the old address cached locally. A **DNS flush** clears this cache so the machine fetches the updated address. This is why Karen's computer (and others on the network) couldn't reach the work website — they were still pointing to the old IP.

The agent clicks **Close** to finalize the ticket.

---

## Step 10 — Ticket Confirmed Closed

<img width="1920" height="955" alt="23_ticket_queue_after_close_karen_gone" src="https://github.com/user-attachments/assets/89b828eb-19f1-4eef-bd30-2bcce9284335" />

After closing, osTicket returns to the **Open Tickets** queue with a green banner: **"Ticket #632319 status changed to Closed."** Karen's ticket is no longer visible in the Open queue — only the default osTicket welcome ticket (#306227) remains.

<img width="1920" height="955" alt="24_closed_tickets_queue_karen_ticket" src="https://github.com/user-attachments/assets/cf2f99bc-fba8-4030-9338-a23106bc93b0" />

Navigating to **Tickets → Closed**, Karen's ticket #632319 now appears in the Closed queue with:
- **Date Closed:** 5/31/26 1:54 AM
- **Subject:** Having an issue visiting the work website
- **From:** Karen
- **Closed By:** Solomon Yohanis

---

## Summary

A complete ticket lifecycle in osTicket:

| Stage | Action |
|---|---|
| **Intake** | End user Karen submitted a ticket through the public Support Center portal |
| **Triage** | Agent Solomon Yohanis reviewed the ticket in the Open queue |
| **Communication** | Agent posted an initial reply acknowledging the issue |
| **Prioritization** | SLA Plan updated from Default SLA to **Sev-B**; Priority updated from Normal to **High** |
| **Resolution** | Agent diagnosed a DNS caching issue and applied a DNS flush |
| **Closure** | Ticket closed with a root cause note; ticket moved to the Closed queue |

Every action — replies, SLA changes, priority updates, and closure — is recorded in the ticket thread, creating a full audit trail that reflects real-world IT help desk workflows.

---

## Conclusion
This project successfully demonstrated osTicket’s full ticket lifecycle in a real-world helpdesk simulation: users submitted issues via the public portal, agents assigned, prioritized, and collaborated using SLAs, departments, and role-based permissions, and tickets were resolved with clear communication and audit trails.



