<p align="center"><img src="../assets/tootsy-logo.svg" alt="Tootsy" height="72"></p>

# 20 ways teams use T4B - Tootsy for Business

Each use case lists the T4B features it relies on and a prompt you can adapt. New to T4B? Start with the [install and use guide](GETTING_STARTED.md).

> **Confidential data:** for anything sensitive, such as payroll, contracts, customer records or source code, use a **local model** (Ollama) or your **company server**, so the content never leaves your network.

| # | Department | Use case |
|---|---|---|
| 1 | Finance | [Month-end variance commentary](#1-finance--month-end-variance-commentary) |
| 2 | Finance | [Invoice and receipt lookup](#2-finance--invoice-and-receipt-lookup) |
| 3 | Sales | [Account research before a meeting](#3-sales--account-research-before-a-meeting) |
| 4 | Sales | [Proposal and RFP drafting](#4-sales--proposal-and-rfp-drafting) |
| 5 | Marketing | [Competitor and market monitoring](#5-marketing--competitor-and-market-monitoring) |
| 6 | Marketing | [Campaign content in many formats](#6-marketing--campaign-content-in-many-formats) |
| 7 | Human Resources | [Policy assistant for employees](#7-human-resources--policy-assistant-for-employees) |
| 8 | Human Resources | [CV screening against a role](#8-human-resources--cv-screening-against-a-role) |
| 9 | Legal | [Contract review and clause comparison](#9-legal--contract-review-and-clause-comparison) |
| 10 | Compliance & Risk | [Regulation tracking and gap checks](#10-compliance--risk--regulation-tracking-and-gap-checks) |
| 11 | IT Operations | [Cloud and cluster health checks](#11-it-operations--cloud-and-cluster-health-checks) |
| 12 | IT Service Desk | [Troubleshooting from tickets and logs](#12-it-service-desk--troubleshooting-from-tickets-and-logs) |
| 13 | Software Engineering | [Code review, explanation and docs](#13-software-engineering--code-review-explanation-and-docs) |
| 14 | Customer Support | [Answer drafting from the knowledge base](#14-customer-support--answer-drafting-from-the-knowledge-base) |
| 15 | Customer Support | [Complaint and feedback analysis](#15-customer-support--complaint-and-feedback-analysis) |
| 16 | Operations & Supply Chain | [Supplier and inventory analysis](#16-operations--supply-chain--supplier-and-inventory-analysis) |
| 17 | Procurement | [Vendor quote comparison](#17-procurement--vendor-quote-comparison) |
| 18 | Executive Office | [Weekly briefing pack](#18-executive-office--weekly-briefing-pack) |
| 19 | Data & Analytics | [Ad-hoc questions over exports](#19-data--analytics--ad-hoc-questions-over-exports) |
| 20 | Project Management | [Meeting notes to action plan](#20-project-management--meeting-notes-to-action-plan) |

---

### 1. Finance — Month-end variance commentary
Explain why actuals differ from budget without retyping numbers into a chat.
- **Uses:** granted folder, **Analyse spreadsheets** (exact SQL totals), **Create documents**
- **Try:** *"In budget-vs-actual-sept.xlsx, list the 5 cost centres with the largest variance in SGD and %, then write a one-paragraph commentary for each and save it as Sept variance.docx."*
- **Why T4B:** the totals are calculated, not estimated by the model, and the output is a ready-to-edit Word file.

### 2. Finance — Invoice and receipt lookup
Find documents in shared folders by what's inside them, including scanned PDFs.
- **Uses:** **Search files** (searches inside PDF and Office files), OCR for scans, **Read file**
- **Try:** *"Find every invoice in this folder that mentions PO-4471, and give me the invoice number, date and total for each."*

### 3. Sales — Account research before a meeting
Build a one-page brief on a prospect in minutes.
- **Uses:** **Web search** and **Read web pages**, a *Sales Researcher* persona, **Create documents**
- **Try:** *"Research Acme Logistics: what they do, recent news from the last 3 months, leadership, and likely priorities. Cite sources. Save as Acme brief.pdf."*

### 4. Sales — Proposal and RFP drafting
Answer RFP questions consistently, drawing on past winning proposals.
- **Uses:** a **Notebook** of past proposals and product sheets, **Search notebooks**, prompt templates
- **Try:** *"Using the Proposals notebook, draft answers to the 12 security questions in this attached RFP (rfp.docx). Mark any answer you're unsure of."*

### 5. Marketing — Competitor and market monitoring
Keep a weekly pulse on competitors without manual browsing.
- **Uses:** **Scheduler** (weekly), **Web search**, webhook to a Teams or Slack channel
- **Try (scheduled every Monday 8:00):** *"Search for news and product announcements from CompetitorA, CompetitorB and CompetitorC in the last 7 days. Summarise each in 2 bullets with links."*

### 6. Marketing — Campaign content in many formats
Turn one brief into on-brand copy for every channel.
- **Uses:** Skills (*Rewrite*, *Shorten*), a *Brand Voice* persona with your style guide, **Compare** to pick the best model's copy
- **Try:** *"From this launch brief, write a LinkedIn post, a 50-word email teaser, three ad headlines (max 30 characters) and a press-release opening paragraph."*

### 7. Human Resources — Policy assistant for employees
Give staff instant, sourced answers about handbook policies.
- **Uses:** a **Notebook** of the employee handbook (full-document mode), an *HR Helper* persona, a local model
- **Try:** *"How many days of parental leave do we offer, and how do I apply?"* The answer cites the policy file it came from.

### 8. Human Resources — CV screening against a role
Shortlist candidates consistently and fairly against stated criteria.
- **Uses:** granted folder of CVs (PDF/Word), **Search files**, **Analyse spreadsheets** for scoring sheets, a local model for privacy
- **Try:** *"For each CV in this folder, score 1–5 against the 6 must-have criteria in job-spec.docx, with one line of evidence per score. Output a table."*
- **Note:** use this to support decisions, not to make them; a person should review every shortlist.

### 9. Legal — Contract review and clause comparison
Spot risky or non-standard clauses quickly.
- **Uses:** attachments (Word and PDF), a *Contract Reviewer* persona with your playbook in a notebook, a local model
- **Try:** *"Compare the attached supplier agreement with our standard terms in the Legal Playbook notebook. List every deviation in liability, termination, data protection and payment terms, with clause numbers."*

### 10. Compliance & Risk — Regulation tracking and gap checks
Understand new rules and check them against internal policy.
- **Uses:** **Read web pages** on the official text, **Search notebooks** over your policies, **Create documents**
- **Try:** *"Read https://… (the regulator's guidance). Then check our Data Policy notebook and list requirements we don't clearly cover yet. Save as gap-analysis.docx."*

### 11. IT Operations — Cloud and cluster health checks
Ask questions about AWS and Kubernetes in plain English, without a separate MCP server.
- **Uses:** **Run commands** (`aws`, `kubectl`). Read-only commands run straight away; anything that changes something asks first
- **Try:** *"List EC2 instances in ap-southeast-1 that are stopped, and show pods in the prod namespace that aren't Running, with their last 20 log lines."*

### 12. IT Service Desk — Troubleshooting from tickets and logs
Diagnose recurring issues faster.
- **Uses:** attachments (log files, ticket exports), **Analyse spreadsheets** for ticket CSVs, **Run commands** for local checks (`ipconfig`, `Test-NetConnection`)
- **Try:** *"From tickets-q3.csv, which 5 issue categories grew the most month over month? For the top one, suggest a knowledge-base article outline."*

### 13. Software Engineering — Code review, explanation and docs
Understand unfamiliar code and keep documentation current.
- **Uses:** granted project folder, **Search files**, **Read file**, **Write file**, Code panel, `git` through **Run commands**
- **Try:** *"Explain how authentication works in this repo, then draft a README section describing it. Show me the diff before writing."*

### 14. Customer Support — Answer drafting from the knowledge base
Give agents accurate draft replies in seconds.
- **Uses:** a **Notebook** of help-centre articles, a *Support Agent* persona, **Quick ask** (Ctrl+Shift+Space) from any app
- **Try:** paste a customer email and ask *"Draft a friendly reply using only our help articles; include the article links."*

### 15. Customer Support — Complaint and feedback analysis
Turn survey and review exports into themes and actions.
- **Uses:** **Analyse spreadsheets** for counts and trends, summarisation, **Create documents** (Excel or Word)
- **Try:** *"In feedback-sept.xlsx, group the comments into themes, count each theme, give 2 example quotes per theme, and save the table as themes.xlsx."*

### 16. Operations & Supply Chain — Supplier and inventory analysis
Catch stock-out risks and late suppliers early.
- **Uses:** **Analyse spreadsheets** (joins across sheets), **Calculator**, **Date & time**
- **Try:** *"Using inventory.xlsx, list SKUs whose stock will run out before the supplier's next delivery date at the current daily usage. Show the days of cover for each."*

### 17. Procurement — Vendor quote comparison
Compare quotes like-for-like and justify a recommendation.
- **Uses:** attachments (several PDF quotes), **Calculator** for exact totals, **Create documents**
- **Try:** *"Compare these 3 attached quotes on unit price, total cost over 3 years, delivery time, warranty and payment terms. Recommend one and explain why, as a one-page Word memo."*

### 18. Executive Office — Weekly briefing pack
Prepare a concise leadership briefing from many sources.
- **Uses:** **Scheduler**, **Web search** (industry news), **Search notebooks** (internal updates), **Create documents** (PDF)
- **Try:** *"Create this week's briefing: top 5 industry news items with links, key internal updates from the Weekly Reports notebook, and 3 decisions needed. Save as briefing-week-41.pdf."*

### 19. Data & Analytics — Ad-hoc questions over exports
Answer quick business questions without opening a BI tool.
- **Uses:** **Analyse spreadsheets** (SQL over CSV and Excel), **Call APIs** for internal REST endpoints (keys saved in Settings), **Create documents** to share the result
- **Try:** *"In orders-2026.csv, what's the average order value by region and month? Flag any month that's more than 20% below the region's average."*

### 20. Project Management — Meeting notes to action plan
Never lose an action item again.
- **Uses:** voice input or pasted notes, **Memory** (team conventions), **Create documents**, **Call APIs** to post tasks to your tracker (with approval)
- **Try:** *"From these notes, list decisions, action items with owner and due date, and open risks. Save as an Excel tracker, then create the action items in Jira through its API."* T4B asks before sending each request.

---

**Tips for rolling T4B out across a company**
- Create a **persona** per team, with the right model, tools and notebook, so people start from a good setup.
- Keep **tool approval** on its default (*Ask before actions*) and **leak protection** on.
- Set a **monthly budget** under **Status → Spending** to track cloud costs.
- Prefer **local or company-hosted models** for regulated or confidential work.
