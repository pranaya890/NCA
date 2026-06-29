## Project Master Specification (PMS)

### Version

1.0

### Status

Design Specification

### Purpose

This document is the master specification for the Personal Finance Management System (PFMS). It defines every architectural decision, functional requirement, database model, workflow, user interface, API behavior, and development guideline required to build the application.

This document is intended to act as the single source of truth for development. Future implementation should follow this specification without introducing assumptions unless explicitly approved.

---

# 1. Project Vision

The Personal Finance Management System is a self-hosted web application that allows a user to manually manage and reconcile personal finances.

Unlike conventional expense trackers, the primary objective of PFMS is financial reconciliation rather than expense recording.

The application continuously determines whether the user's current financial assets match the expected balances calculated from all recorded financial activities.

The system is designed to answer one fundamental question:

**"Do my current assets accurately reflect all of my recorded income, expenses, and transfers?"**

---

# 2. Primary Objective

Maintain an accurate financial ledger by validating:

Expected Assets =  
Opening Assets

- Income  
    − Expenses  
    ± Asset Transfers  
    ± Manual Balance Adjustments (if any)
    

If the calculated balance differs from the user's actual balances, the system reports a discrepancy.

---

# 3. Core Philosophy

The application never connects to banks.

The application never imports transactions automatically.

The application never scrapes bank statements.

Every financial event is manually entered by the user.

The application behaves as a personal accounting ledger rather than a banking application.

---

# 4. Major Features

• Authentication  
• Dashboard  
• Asset Management  
• Income Management  
• Expense Management  
• Asset Transfers  
• Categories  
• Reports  
• Analytics  
• Financial Verification Engine  
• Settings

---

# 5. Assets

Assets represent places where money currently exists.

Examples

Cash

Wallet

Nabil Bank

Nepal SBI

eSewa

Khalti

IME Pay

Gold

Cryptocurrency

Each asset contains

• Name  
• Type  
• Current Balance  
• Opening Balance  
• Description  
• Active Status

The system stores balances only.

No account numbers.

No bank credentials.

No transaction synchronization.

---

# 6. Asset Types

Cash

Physical Wallet

Bank Balance

Digital Wallet

Investment

Other

---

# 7. Income

Each income record contains

Income ID

Amount

Category

Destination Asset

Date

Description

Example

Salary

Amount

Rs. 50,000

Destination

Nabil Bank

---

# 8. Expense

Each expense contains

Expense ID

Amount

Category

Source Asset

Date

Description

Example

Food

Amount

Rs. 450

Source

Cash

---

# 9. Asset Transfer

Transfers move money between assets.

Transfers never affect income.

Transfers never affect expenses.

Example

Cash

↓

eSewa

Rs. 2,000

Both balances update automatically.

---

# 10. Categories

Income Categories

Salary

Freelance

Investment

Refund

Gift

Bonus

Expense Categories

Food

Transport

Shopping

Internet

Utilities

Rent

Education

Sports

Medical

Entertainment

Miscellaneous

Categories are editable.

---

# 11. Financial Verification Engine

The verification engine is the heart of the application.

Formula

Expected Asset Balance

=

Opening Balance

Income

Expenses

Incoming Transfers

Outgoing Transfers

Compare

Expected Balance

Actual Balance

If

Expected ≠ Actual

Display

Difference

Percentage

Possible reasons

Status

Verified

or

Needs Attention

---

# 12. Dashboard

Cards

Net Assets

Monthly Income

Monthly Expenses

Savings

Financial Difference

Verification Status

Recent Transactions

Recent Transfers

Charts

Income vs Expense

Expense Categories

Monthly Trends

Asset Distribution

Cash Flow

---

# 13. PostgreSQL

Stores

Users

Assets

Income

Expenses

Transfers

Categories

Settings

Authentication

Relationships

Reports

---

# 14. MongoDB

Stores

Dashboard cache

Analytics snapshots

Activity logs

Future AI insights

Application logs

System events

Future OCR

Future notification history

MongoDB intentionally stores flexible and semi-structured data rather than transactional records.

---

# 15. Docker Architecture

Containers

Nginx

↓

Django Backend

↓

PostgreSQL

MongoDB

Redis

Celery Worker

Docker Compose manages all services.

Each container has a single responsibility.

---

# 16. Folder Structure

backend/

frontend/

docker/

nginx/

postgres/

mongodb/

media/

static/

docs/

tests/

docker-compose.yml

README.md

.env

---

# 17. REST API

Authentication

/api/login

/api/logout

/api/register

Assets

GET /assets

POST /assets

PUT /assets/{id}

DELETE /assets/{id}

Income

Expense

Transfers

Dashboard

Reports

Analytics

Settings

---

# 18. UI Design Principles

Minimal

Responsive

Dark Mode

Desktop First

Clean Dashboard

Fast Navigation

Consistent Colors

No unnecessary animations

---

# 19. Security

JWT Authentication

Password Hashing

CSRF Protection

Rate Limiting

Input Validation

Role-based Authorization

Secure Docker Networking

Environment Variables

---

# 20. Coding Standards

Python

PEP 8

Black Formatter

isort

flake8

REST Naming Conventions

Service Layer Architecture

Repository Pattern where appropriate

---

# 21. Development Stack

Backend

Django

Django REST Framework

Frontend

HTML

Tailwind CSS

JavaScript

Database

PostgreSQL

MongoDB

Cache

Redis

Background Jobs

Celery

Containerization

Docker

Docker Compose

Version Control

Git

GitHub

---

# 22. Future Scope

Budget Planner

Recurring Transactions

AI Spending Prediction

Financial Advisor

Goal Tracking

Receipt OCR

Email Reports

Multi-user Support

Bank API Integration (Optional)

Mobile Application

Machine Learning Analytics

---

# 23. Non-Goals (Version 1)

No automatic bank synchronization.

No receipt uploads.

No OCR.

No stock market APIs.

No cryptocurrency price APIs.

No loan amortization calculations.

No multi-currency support.

These features may be introduced in future versions but are intentionally excluded from Version 1 to keep the system focused on reliable manual financial reconciliation.

---

# 24. Development Philosophy

The project should prioritize correctness over complexity. Every transaction, transfer, and balance update must preserve financial consistency. Simplicity, maintainability, and extensibility should guide all architectural and implementation decisions. The codebase should be modular, thoroughly documented, and designed to accommodate future features without requiring major redesigns.