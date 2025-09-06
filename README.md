# osticket-post-install-config
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket Post-Installation Configuration (Admin Setup)

This guide walks you through a **basic post-installation configuration** of the open-source help desk ticketing system **osTicket**. The goal is to prepare the system so you can create and work **mock tickets** that mirror real help desk workflows.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

## Table of Contents
- [Why Configure Before Creating Tickets](#why-configure-before-creating-tickets)
- [Getting Started — Log In and Panel Switch](#getting-started--log-in-and-panel-switch)
- [Admin Panel Overview (What You Can Configure)](#admin-panel-overview-what-you-can-configure)
- [STEP 1 — Configure Roles](#step-1--configure-roles)
- [STEP 2 — Configure Departments](#step-2--configure-departments)
- [STEP 3 — Configure Teams](#step-3--configure-teams)
- [STEP 4 — Configure Agents](#step-4--configure-agents)
- [STEP 5 — Configure Users](#step-5--configure-users)
- [STEP 6 — Configure SLAs](#step-6--configure-slas)
- [STEP 7 — Configure Help Topics](#step-7--configure-help-topics)
- [Summary / Next Steps](#summary--next-steps)

---

### Why Configure Before Creating Tickets
**Short answer:** Configuration establishes the **rules, access, and workflows** the system follows.  
**Why it matters:** Proper setup ensures:
- The right **roles/permissions** control who can see and do what.
- **Departments/teams** receive the correct tickets.
- **SLAs** and priorities drive response/resolution expectations.
- **User settings** and visibility are secure and realistic.

Skipping configuration leads to misrouted tickets, incorrect access, and unrealistic practice.

---

### Getting Started — Log In and Panel Switch
Log in to the **Admin Panel** with the admin account you created during installation:  
[http://localhost/osTicket/scp/login.php](http://localhost/osTicket/scp/login.php)

<a href="http://localhost/osTicket/scp/login.php" target="_blank" rel="noopener">osTicket Login</a>

In osTicket you can toggle between:
- **Admin Panel** (system configuration)
- **Agent Panel** (day-to-day ticket work)

For this guide, you’ll primarily use the **Admin Panel**.

---

### Admin Panel Overview (What You Can Configure)
- **Roles & Permissions:** Define what agents can view/do.
- **Departments:** Control visibility and routing by org group.
- **Teams:** Cross-department collaboration groups.
- **Agents:** The staff who work tickets; assign roles/departments/teams.
- **SLAs:** Timeframes for response/resolution and overdue rules.
- **Help Topics:** Categories that guide routing and priority.
- **User Settings & System Config:** Registration, email, alerts, branding.
- **Reports & Logs:** Performance, histories, auditing.

---

### STEP 1 — Configure Roles
**Why:** Roles define **permissions** (view, reply, assign, manage) that agents have **per department**. Clear roles prevent over-permissioning and protect data.

**Instructions:**  
Admin Panel → **Agents** → **Roles**  
- **Add** new roles.  
- Use **More** to enable/disable/delete.  
- Click a role to set permissions for **Tickets**, **Tasks**, **Knowledgebase**.

**Tips:** Start with roles like *Help Desk*, *Supervisor*, *Admin* and grant only what’s needed.

---

### STEP 2 — Configure Departments
**Why:** Departments define **ticket visibility and assignment** scope (e.g., Help Desk, Networking, CIS Admins). They keep workflows organized and tickets routed correctly.

**Instructions:**  
Admin Panel → **Agents** → **Departments**  
- **Add** new departments.  
- Use **More** to enable/disable/archive/delete.  
- Click a department to adjust settings and access.

**Tips:** Map departments to real org units so mock tickets feel realistic.

---

### STEP 3 — Configure Teams
**Why:** Teams allow **cross-department collaboration** on specific issues/projects (e.g., an “Online Banking” team that includes Help Desk + CIS Admins).

**Instructions:**  
Admin Panel → **Agents** → **Teams**  
- **Add** new teams.  
- Use **More** to enable/disable/delete.  
- Click a team to adjust members and behavior.

**Tips:** Use teams when tickets often require multiple groups.

---

### STEP 4 — Configure Agents
**Why:** Agents are the staff who **work tickets**. Assigning roles, departments, and teams ensures the **right people** see and act on the **right tickets**.

**Instructions:**  
Admin Panel → **Agents**  
- **Add** new agents.  
- **More:** enable/disable, reset permissions, change departments, export, delete.  
- Click an agent to edit **account**, **access**, **permissions**, **teams**.

**Tips:** Least privilege: grant only what the agent needs.

---

### STEP 5 — Configure Users
**Why:** Users are the **ticket owners** (end customers). They submit requests and track their own tickets; they don’t access admin/agent panels.

**Instructions:**  
**Agent Panel** → **Users**  
- **Add** individual users.  
- **Import** users via copy/paste list (name + email) or **CSV** (more fields).  
- **More:** add to organizations, send password resets, register, lock/unlock, delete.

**Notes:** Deleting a user typically requires deleting their tickets too (data linkage).

---

### STEP 6 — Configure SLAs
**Why:** SLAs define **response/resolution timeframes** (e.g., critical vs normal). They drive priority, overdue status, and performance tracking.

**Instructions:**  
Admin Panel → **Manage** → **SLA**  
- **Add New** SLA Plans.  
- **More:** enable/disable/delete.  
- Click an SLA to adjust schedules and targets.

**Considerations:**  
- Align schedules to **business hours** and **time zones**.  
- Use stricter targets for **high-impact** issues.  
- Monitor breaches and refine staffing/process if SLAs slip.

---

### STEP 7 — Configure Help Topics
**Why:** Help Topics categorize issues (e.g., “Password Reset,” “Equipment Request,” “Business Critical Outage”) and guide **routing**, **priority**, and **reporting**.

**Instructions:**  
Admin Panel → **Manage** → **Help Topics**  
- **Add New** Help Topics.  
- **More:** enable/disable/archive/delete.  
- Click a topic to edit **parent/subtopic**, **priority**, **SLA**.

**Tips:**  
- Use **parent topics** with **subtopics** for clarity.  
- Tie topics to **departments/teams** and **SLA plans** where appropriate.

---

### Summary / Next Steps
You’ve configured the core building blocks that control **who** sees **what**, **how** tickets are routed, and **how fast** they must be handled.  
**Now you’re ready to practice with mock tickets** that behave like real requests:
1. Create users (or import a list).  
2. Submit tickets under different **Help Topics**.  
3. Watch routing to **Departments/Teams** and ensure **SLAs** behave as expected.  
4. Adjust roles, topics, and SLAs based on what you learn.

Happy ticketing!


