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
- [STEP 6 — Configure SLAs](#step-6--configure-schedules-and-slas)
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

<img width="929" height="685" alt="0 1 nav to login page" src="https://github.com/user-attachments/assets/fc902708-2cd4-4310-a20c-3f23a22ac1fd" />

In osTicket you can toggle between:
- **Admin Panel** (system configuration)
- **Agent Panel** (day-to-day ticket work)
  
<img width="351" height="41" alt="0 2 admin vs agent" src="https://github.com/user-attachments/assets/77048572-879c-42c3-bfa1-e5ae63964633" />

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
**Why:** Roles define **permissions** (view, reply, assign, manage) that agents have. Clear roles prevent over-permissioning and protect data.

**Outline:**  
Admin Panel → **Agents** → **Roles**  
- **Add** new roles.  
- Use **More** to enable/disable/delete.  
- Click a role to set permissions for **Tickets**, **Tasks**, **Knowledgebase**.

<p>
 <img width="956" height="341" alt="1 1 configure roles2" src="https://github.com/user-attachments/assets/1ce90dd8-7dee-4b10-96e7-725e3278971a" />
</p>

**Instructions:** 
Create roles **Agent (Tier 1)**, **Maintenance Tech** and **Supervisor** and grant different permissions for each role.
- **Agent (Tier 1)**
  - Permissions → Assign, Close, Create, Link, Mark as Answered, Post Reply, Release.
  - Tasks → Assign, Close, Create, Post Reply.
  - Knowledgebase → None.
- **Maintenance Tech**
  - Permissions → Close, Create, Link, Mark as Answered, Post Reply, Release.
  - Tasks → Close, Create, Post Reply.
  - Premade → None.
- **Supervisor**
  - Permissions → All permissions except delete.
  - Tasks → All tasks except delete.
  - Knowledgebase → Premade.

<img width="956" height="702" alt="1 3 set permissions" src="https://github.com/user-attachments/assets/349459cf-3e22-4c9d-a3d3-013bd7e5724b" />

---

### STEP 2 — Configure Departments
**Why:** Departments define **ticket visibility and assignment** scope (e.g., Help Desk, Networking, Security). They keep workflows organized and tickets routed correctly.

**Outline:**  
Admin Panel → **Agents** → **Departments**  
- **Add** new departments.  
- Use **More** to enable/disable/archive/delete.  
- Click a department to adjust settings and access.

<p>
<img width="955" height="289" alt="2 1 configure departments2" src="https://github.com/user-attachments/assets/08aba93f-90b4-4920-acc6-599743551912" />
</p>

**Notes:**
- The *access* tab allows you to add agents to each department, we will add agents later.
- You can assign *SLAs* later after they have been created.
- Departments can be assigned as a *sub-department* by selecting a *parent department*.
- Map departments to real organization units so mock tickets feel realistic.
  
**Instructions:** 
Create three deparments **Help Desk**, **Maintenance** and **Systems**.
- **Help Desk**
  - Rename *Support* to *Help Desk*
- **Maintenance**
  - Keep as is (comes already created when setting up osTicket).
- **Systems**
  - Parent → Top-Level Department

<img width="956" height="883" alt="2 2 configure department settings" src="https://github.com/user-attachments/assets/8cc6a3f5-b338-4633-aa9a-d0a1df403f8c" />

---

### STEP 3 — Configure Teams
**Why:** 
Teams allow **cross-department collaboration** on specific issues/projects (e.g., an “Online Banking” team that includes Help Desk + Sysadmin agents).

**Outline:**  
Admin Panel → **Agents** → **Teams**  
- **Add** new teams.  
- Use **More** to enable/disable/delete.  
- Click a team to adjust team information and members.

<p>
<img width="955" height="262" alt="3 1 configure teams2" src="https://github.com/user-attachments/assets/97a399cd-ddd2-4661-be82-d63ffa4fbc45" />
</p>

**Notes:**
- *Level I Support* comes already created when setting up osTicket, **delete** it to simplify the mock ticket workflow.
- You can add agents to these teams after they have been entered.

**Instructions:** 
Create two teams like **Accounts and Passwords** and **PC Fix**.

<img width="955" height="425" alt="3 2 add members to teams" src="https://github.com/user-attachments/assets/38745d64-ab69-491e-beb5-9da6b266112c" />

---

### STEP 4 — Configure Agents
**Why:** Agents are the staff who **work tickets**. Assigning roles, departments, and teams ensures the **right people** see and act on the **right tickets**.

**Outline:**  
Admin Panel → **Agents**  
- **Add** new agents.  
- **More:** enable/disable, reset permissions, change departments, export, delete.  
- Click an agent to edit **account**, **access**, **permissions**, **teams**.

<p>
<img width="953" height="303" alt="4 1 configure agents2" src="https://github.com/user-attachments/assets/d529a973-ab87-4c07-b93f-bdc7ac181178" />
</p>

**Instructions:**
Create three agents and configure their **accounts**, **access**, **permissions** and **teams**.
- Under **Account**, give them a name, email (can be a fake email for mock tickets), username, and set a password.
- When setting the password:
  1. Uncheck "Send the agent a password reset email"
  2. Enter a New Password
  3. Uncheck "Require password change at next login, Click **Update**.

  - **Agent 1** – *Agent (Tier1)*
    - **Access**
      - Assign to department **Help Desk** and set the role to **Agent (Tier 1)**
    - **Permissions**
      - **Users** → Create, Edit, Manage Account, User Directory
      - **Organizations** → Create, Edit
      - **Knowledgebase** → None
      - **Miscellaneous** → Agent
    - **Teams** → **Accounts and Passwords** and **PC Fix**
   
  - **Agent 2** – *Maintenance Worker*
    - **Access**
      - Assign to department **Maintenance** and set the role to **Maintenance Tech**
    - **Permissions**
      - **Users** → User Directory
      - **Organizations** → None
      - **Knowledgebase** → None
      - **Miscellaneous** → None
    - **Teams** → None
   
  - **Agent 3** – *Supervisor*
    - **Access**
      - Assign to department **Help Desk** and set the role to **Supervisor**
      - Assign to extedned access to department **Systems** and set the role to **Supervisor**
    - **Permissions**
      - **Users** → Create, Edit, Manage Account, User Directory
      - **Organizations** → Create, Edit
      - **Knowledgebase** → FAQ
      - **Miscellaneous** → Agent, Banlist, Department, Search, Stats
    - **Teams** → **Accounts and Passwords** and **PC Fix**

<img width="956" height="925" alt="4 2 agent settings" src="https://github.com/user-attachments/assets/ad89ce49-24ea-405f-a448-a59802652b5a" />

---

### STEP 5 — Configure Users
**Why:** Users are the **ticket owners** (end customers). They submit requests and track their own tickets; they don’t access admin/agent panels.

**Outline:**  
**Agent Panel** → **Users**  
- **Add** individual users.  
- **Import** users via copy/paste list (name + email) or **CSV** (more fields).  
- **More:** add to organizations, send password resets, register, lock/unlock, delete.

<p>
<img width="953" height="301" alt="5 1 add users2" src="https://github.com/user-attachments/assets/753ed07e-682f-4232-a5ff-466c4ee91587" />
</p>

**Notes:**
- Deleting a user typically requires deleting their tickets too (data linkage).

**Instructions:** 
Create one individual user using any name and email (can be a fake email for mock tickets) you like.

<img width="638" height="359" alt="5 2 import copy-paste" src="https://github.com/user-attachments/assets/2412c67e-cb70-4de5-aea8-3a0be2c693ec" />

<img width="644" height="381" alt="5 3 import csv" src="https://github.com/user-attachments/assets/76fc22d7-b93a-4897-91c6-aab97deae224" />

---

### STEP 6 — Configure SLAs
**Why:** SLAs define **response/resolution timeframes** (e.g., critical vs normal). They drive priority, overdue status, and performance tracking.

**Outline:**  
Admin Panel → **Manage** → **SLA**  
- **Add New** SLA Plans.  
- **More:** enable/disable/delete.  
- Click an SLA to adjust schedules and targets.

<p>
<img width="955" height="260" alt="6 1 configure sla2" src="https://github.com/user-attachments/assets/dae4344a-f4e5-46c1-9bde-1d796c618822" />
</p>

**Notes:**  
- Align schedules to **business hours** and **time zones**.  
- Use stricter targets for **high-impact** issues.  
- Monitor breaches and refine staffing/process if SLAs slip.

**Instructions:**
Create five SLA plans. SLAs inside of osTicket define Grace Periods as the resolution target which is not a universal practice.
- **Default SLA** → Business Hours, 16h Grace Period, Transient
- **P1 Critical** → 24x7 Schedule, 4h Grace Period, Non-transient
- **P2 High** → Business Hours, 8h Grace Period, Non-transient
- **P3 Normal** → Business Hours, 24h Grace Period, Non-transient
- **P4 Low** → Business Hours, 40h Grace Period, Non-transient



---

### STEP 7 — Configure Help Topics
**Why:** Help Topics categorize issues (e.g., “Password Reset,” “Equipment Request,” “Business Critical Outage”) and guide **routing**, **priority**, and **reporting**.

**Outline:**  
Admin Panel → **Manage** → **Help Topics**  
- **Add New** Help Topics.  
- **More:** enable/disable/archive/delete.  
- Click a topic to edit **parent/subtopic**, **priority**, **SLA**.

<p>
<img width="953" height="376" alt="7 1 configure help topics2" src="https://github.com/user-attachments/assets/2f226350-a656-4002-a4d1-fbe6e6678c4c" />
</p>

**Notes:**  
- Use **parent topics** with **subtopics** for clarity.  
- Tie topics to **departments/teams** and **SLA plans** where appropriate.

**Instructions:**
Create seven **Help Topics** and assign **SLAs**, **Priority Levels**, **Departments** and **Teams**. Three will parent topics (Top-Level-Topic) and four will be child topics (Subtopic).
- Leave **Feed Back** and **General Inqury** as is. Delete **Report a Problem / Access Issue**.
- Add Top-Level-Topic **Service Outage** → Department - Systems, Priority - Emergency, SLA - P1, Team - None
- Edit **Report a Problem** → Department - Help Desk, Priority - Normal, SLA - Default SLA, Team - None
  - Add Subtopic **Report a Problem / Hardware** → Department - Help Desk, Priority - Normal, SLA - P3, Team - PC Fix
  - Add Subtopic **Report a Problem / Software** → Department - Help Desk, Priority - Normal, SLA - P3, Team - PC Fix
- Add Top-Level-Topic **Account Issues** → Department - Help Desk, Priority - Normal, SLA - Default SLA, Team - None
  - Add Subtopic **Account Issues / Password Reset** → Department - Help Desk, Priority - Normal, SLA - P3, Team - Accounts and Passwords
  - Add Subtopic **Account Issues / Account Lockout** → Department - Help Desk, Priority - HighAccount, SLA - P2, Team - Accounts and Passwords

---

### Summary / Next Steps
You’ve configured the core building blocks that control **who** sees **what**, **how** tickets are routed, and **how fast** they must be handled.  
**Now you’re ready to practice with mock tickets** that behave like real requests:
1. *Optional* Create more users (or import a list).  
2. Submit tickets under different **Help Topics**.  
3. Watch routing to **Departments/Teams** and ensure **SLAs** behave as expected.  
4. Adjust roles, topics, and SLAs based on what you learn.

Happy ticketing!
