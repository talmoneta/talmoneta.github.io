# TAU Computing Division — IT / infrastructure answers (2026)

**Route:** Questions from Tech for Cancer (Tal) → Haia → university IT (multiple units).  
**Respondent:** Yochai — Team leader, Microsoft Infrastructures team, Computing Division, Tel Aviv University.  
**Context:** Ben-David lab portal / storage / VPN / M365 / LLM policy.

---

## Full message (as received)

> Hello Haia.  
> My name is Yochai, and I'm team leader of the Microsoft Infrastructures team in the Computing Division.  
> These are a lot of questions, that touch a lot of subjects that aren't strictly related, and therefore are handled by different people here in the Computing Division.  
> I'll try to answer them to the best of my ability and knowledge.

### 1 — Website hosting

The Computing Division does have website hosting services. It really depends how the application is built and what technologies should it run on to determine if our hosting services and which, can host your application. It is also very important to know in advanced if the website should be a publicly available website, or only accessible on campus. Publicly available websites hosted under the university domain (tau.ac.il) need to conform to international standards like GDPR (which have privacy and accessibility demands), and require our information security teams' penetration testing approval.

### 2 — Public vs internal

As previously stated - public facing websites need to conform to requirements. The only requirement which is excluded when the website is not publicly facing are the GDPR requirements. Pen-testing might still be required.

### 3 — VPN / client vs server

This is really more of an application design decision. If what is writing to our central storage is the website, the hosting service that is running it will have access to it even if you're not connected via VPN (which suggests that the site IS public facing). If what is writing to our central storage is the browser, then a VPN connection is needed and probably some form of authentication. This is the difference between client-side and server-side. I can't really help here without knowing what your application does.

### 4 — File servers / OneDrive / SMB

This really depends on how the lab shares and file servers allow access. Communications-wise - I don't see a problem, but I'm not the decision maker on these issues. Each hosting service has it's own requirements, assuming your appication passes pen-testing. Regarding M365/OneDrive access from the app - this needs to be addressed per case. For files - the simplest way to go is SMB on the university central storage IMO.

### 5 — Compute vs file server

Again - each of our hosting services has it's own available features. Determining which infrastructure is right for you starts at understanding the technology running the website (simple HTML is nice, but backend is not clear).

### 6 — Authentication

How you implement authentication is your programmers choice.

### 7 — Research data → external LLMs

Unfortunately I cannot help you here, as I'm not the man to ask. Try emailing **infosec@tauex.tau.ac.il** However, I'm pretty sure sending research data to LLMs is strictly forbidden.

### 8 — Claude / team AI (see 7)

See 7.

### 9 — API keys / usage-based billing

I'm pretty sure the computing division doesn't sell subscriptions that allow API key usage, as those are paid by usage, and not by a fixed price.

### 10 — (unclear question in original thread)

Sorry, lost you here.

### Closing

> I hope that these answers help you on your way to understanding what is best for you, and I hope I didn't cause more confusion than you previously had. I do think that before understanding what is possible to achieve on the university infrastructure, that you define more strictly what is required for your application to run.

---

## Working summary (for product decisions)

| Topic | Takeaway |
|--------|-----------|
| Hosting | Yes, services exist; **match stack to offering**; **public vs campus-only** drives GDPR + pen-test scope. |
| Public tau.ac.il | GDPR-style requirements + **infosec pen-test** likely; internal may drop GDPR but **pen-test may still apply**. |
| Storage access model | **Server-side writes** → hosting has path to storage (often implies public-facing site); **browser writes** → **VPN + auth** typical. Need a concrete architecture doc. |
| SMB / files | **SMB on central storage** called out as simplest for files; lab share specifics = **other owners**; M365/Graph **per case**. |
| Auth | **Our choice** as implementers (SSO vs allowlist, etc.). |
| LLMs / APIs | **Escalate to infosec@tauex.tau.ac.il**; respondent’s working assumption: **sending research data to LLMs strictly forbidden**. |
| Usage-based API keys | **Not sold** by Computing Division as a fixed subscription; usage billing is a different procurement path. |
| Next | **Tighten requirements**: stack, public vs internal, who writes to storage (browser vs server), then re-engage hosting + pen-test track. |

---

**Source:** Email/thread relayed by Haia Khoury to Tal (Tech for Cancer), 2026.
