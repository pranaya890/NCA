
I wouldn't call this just a "Project Vision." I'd call it the **Project Blueprint v1.0**. This document is written so that both a human developer and an AI coding assistant can understand exactly what needs to be built.

---

# PHASE 1: PROJECT BLUEPRINT v1.0

## 1. Project Name

**Personal Finance Management System (PFMS)**

---

# 2. Project Goal

## Primary Goal

Develop a self-hosted Personal Finance Management System that allows users to manually record and manage their financial activities while ensuring that their recorded financial transactions reconcile with their actual asset balances.

Unlike conventional expense trackers, this system is designed around **financial reconciliation** rather than simple transaction logging.

The application should continuously determine whether the user's financial records are internally consistent and identify discrepancies when expected balances do not match actual balances.

---

# 3. Project Philosophy

This application is intended to function as a **personal accounting ledger** rather than a banking application.

The system will not automatically connect to banks, digital wallets, or financial institutions. Instead, all financial events are entered manually by the user. This ensures that the user remains fully aware of every financial activity while also making the application independent of third-party APIs.

The emphasis is on transparency, accuracy, and maintainability.

---

# 4. Target Users

### Version 1

Single user only.

Future versions may support multiple users and organizations.

---

# 5. Primary Problem Statement

Many expense tracking applications allow users to record income and expenses but do not verify whether the recorded data actually corresponds to the user's real financial position.

For example:

A user records:

- Salary: Rs. 50,000
    
- Food: Rs. 4,000
    
- Rent: Rs. 12,000
    

The application simply stores these transactions.

However, it does not answer questions such as:

- Does the user's remaining money actually exist?
    
- Are all balances correct?
    
- Has any transaction been forgotten?
    
- Is there a discrepancy between recorded transactions and actual assets?
    

PFMS is designed specifically to answer these questions.

---

# 6. Main Objective

Maintain complete consistency between

- Income
    
- Expenses
    
- Asset Transfers
    
- Asset Balances
    

and automatically identify inconsistencies.

---

# 7. Core Accounting Principle

The application is built around a simple accounting rule:

```
Opening Assets
+ Income
- Expenses
+ Incoming Transfers
- Outgoing Transfers
= Expected Asset Balance
```

The expected balance is then compared with the actual balance entered by the user.

---

# 8. Scope of Version 1

Version 1 includes:

- Authentication
    
- Asset Management
    
- Income Management
    
- Expense Management
    
- Asset Transfers
    
- Categories
    
- Dashboard
    
- Reports
    
- Financial Verification Engine
    
- Docker Deployment
    

Version 1 intentionally excludes:

- Bank synchronization
    
- Receipt uploads
    
- OCR
    
- AI assistant
    
- Loan management
    
- Investment price tracking
    
- Multi-user support
    
- Multi-currency
    

---

# 9. Functional Modules

The application consists of the following modules:

### Authentication

Handles user registration, login, logout, and account management.

---

### Asset Management

Maintains all places where money exists.

Examples:

- Cash
    
- Wallet
    
- Nabil Bank Balance
    
- eSewa Balance
    
- Khalti Balance
    

Important:

The application stores balances only.

It does **not** connect to the actual services.

---

### Income Module

Responsible for recording every source of income.

Every income must increase exactly one asset.

Example:

Salary

↓

Destination Asset

↓

Nabil Bank

---

### Expense Module

Responsible for recording every expenditure.

Every expense decreases exactly one asset.

Example:

Lunch

↓

Source Asset

↓

Cash

---

### Asset Transfer Module

Transfers money between assets.

Example

Cash

↓

eSewa

This affects balances but **not** income or expenses.

---

### Categories

Editable categories for income and expenses.

---

### Dashboard

Displays

- Net Assets
    
- Monthly Income
    
- Monthly Expense
    
- Verification Status
    
- Asset Distribution
    
- Recent Transactions
    

---

### Reports

Monthly

Yearly

Category

Asset

Income

Expense

---

### Verification Engine

The heart of the system.

Calculates expected balances.

Compares them with current balances.

Displays discrepancies.

---

# 10. Assets

Assets represent locations where money currently exists.

Each asset contains:

- Name
    
- Asset Type
    
- Opening Balance
    
- Current Balance
    
- Description
    
- Status
    

Asset Types:

- Cash
    
- Wallet
    
- Bank Balance
    
- Digital Wallet
    
- Investment
    
- Other
    

---

# 11. Income

Each income contains:

- Amount
    
- Date
    
- Category
    
- Destination Asset
    
- Description
    

Rules:

Income always increases one asset.

---

# 12. Expense

Each expense contains:

- Amount
    
- Date
    
- Category
    
- Source Asset
    
- Description
    

Rules:

Expense always decreases one asset.

---

# 13. Asset Transfer

Contains:

- Source Asset
    
- Destination Asset
    
- Amount
    
- Date
    
- Description
    

Rules:

Transfers never change total wealth.

---

# 14. Business Rules

Every financial event must satisfy these rules:

### Rule 1

Income must always reference exactly one destination asset.

---

### Rule 2

Expense must always reference exactly one source asset.

---

### Rule 3

Transfers must contain both source and destination assets.

---

### Rule 4

Negative balances are configurable. Some asset types (e.g., cash) may disallow them.

---

### Rule 5

Deleting a transaction must automatically update calculated balances.

---

### Rule 6

Editing historical transactions must trigger recalculation of all affected balances.

---

### Rule 7

Transactions are immutable from an accounting perspective; edits create audit history.

_(For Version 1, we may simply update the record and add full audit history in Version 2.)_

---

# 15. Technology Decisions

Backend:

- Django
    

API:

- Django REST Framework
    

SQL Database:

- PostgreSQL
    

NoSQL Database:

- MongoDB
    

Cache:

- Redis
    

Background Tasks:

- Celery
    

Reverse Proxy:

- Nginx
    

Containerization:

- Docker
    

Version Control:

- Git
    

---

# 16. Why PostgreSQL?

PostgreSQL stores:

- Users
    
- Assets
    
- Transactions
    
- Categories
    
- Reports
    
- Authentication
    

Reason:

Financial data requires ACID transactions and strong consistency.

---

# 17. Why MongoDB?

MongoDB stores:

- Dashboard snapshots
    
- Activity logs
    
- Analytics cache
    
- Future AI outputs
    
- Future notifications
    

Reason:

These are flexible, document-oriented, and may evolve over time.

---

# 18. Docker Philosophy

Every major service runs in its own container.

Planned containers:

1. Nginx
    
2. Django Backend
    
3. PostgreSQL
    
4. MongoDB
    
5. Redis
    
6. Celery Worker
    

Docker Compose orchestrates the entire environment.

---

# 19. Coding Principles

- Thin views, business logic in services.
    
- Atomic financial operations.
    
- Clear separation between SQL and NoSQL responsibilities.
    
- Reusable components.
    
- Comprehensive logging.
    
- Type hints and docstrings.
    
- High test coverage.
    

---

# 20. Success Criteria

Version 1 will be considered successful if it can:

- Record all income, expenses, and transfers.
    
- Correctly update asset balances.
    
- Verify expected vs. actual balances.
    
- Display meaningful dashboards and reports.
    
- Run entirely within Docker.
    
- Use PostgreSQL and MongoDB appropriately.
    
- Be straightforward to extend with future features.
    

---

## One Important Suggestion Before We Proceed

There is **one architectural decision** I'd like us to make now because it will affect the entire project:

### Should the application maintain balances in two ways?

For example, each asset could have:

- **Actual Balance** — entered manually by the user to reflect the real-world balance.
    
- **Calculated Balance** — computed by the system from the opening balance, income, expenses, and transfers.
    

The Verification Engine would compare these two values:

```
Calculated Balance = Rs. 24,350
Actual Balance     = Rs. 24,000

Difference         = Rs. 350

Status             = Needs Reconciliation
```

I strongly recommend this design because it turns your project into a true reconciliation system rather than just an expense tracker. It also aligns perfectly with your original goal of checking whether the financial records match reality. If we adopt this now, we can build the rest of the architecture around it consistently.