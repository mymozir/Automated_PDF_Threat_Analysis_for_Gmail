# Email Security Gateway Prototype

## About

This is an educational project that simulates an email attachment security gateway for Gmail.

The system automatically processes incoming emails with PDF attachments, analyzes them using a rule-based detection pipeline, and applies AI-assisted verification when necessary. Based on the analysis result, each message is classified as:

- CLEAN
- VERIFY
- MALWARE

The project was created to explore practical concepts of email security, automated threat detection, and decision-making pipelines.

![Overview of the application](img/Снимок%20экрана%202026-06-17%2184141.png)

*Figure 1 — Overall view of the application*

---

## Features

- Automatic processing of Gmail messages with PDF attachments via Google Apps Script
- Static analysis of PDF files at the byte and structure level
- Detection of potentially dangerous PDF features:
  - JavaScript execution
  - OpenAction
  - Additional Actions (AA)
  - Launch actions
  - SubmitForm / ImportData operations
- URL analysis:
  - URL shorteners (e.g., bit.ly, tinyurl)
  - IP-based URLs
  - Punycode domains
  - Suspicious use of `@` in URLs
- Rule-based classification system:
  - CLEAN
  - VERIFY
  - MALWARE

![Label routing and message forwarding](img/photo_5303173086368702664_y.jpg)

*Figure 2 — Routing emails by labels and forwarding logic*

- AI-assisted verification for ambiguous cases (VERIFY stage only)
- Gmail labeling and routing system:
  - `_SAFE`
  - `_VERIFY`
  - `_QUARANTINE`
- Protection against duplicate processing and forwarding loops
- Structured reporting of analysis results

---

## Architecture

The system consists of two main components:

- Google Apps Script (Gmail automation layer)
- Backend analysis service (PDF parsing + rule engine + AI verification)

![Deployment on Render.com](img/photo_5303173086368702680_y.jpg)

*Figure 3 — Backend deployment on Render.com*

---

## Workflow

```text
Incoming Gmail message
        │
        ▼
Google Apps Script trigger
        │
        ▼
Extract PDF attachment
        │
        ▼
Backend analysis request
        │
 ┌───────────────┐
 │               │
 ▼               ▼
Rule-based checks   AI verification (only if needed)
 │
 ▼
Final classification:
CLEAN / VERIFY / MALWARE
 │
 ▼
Apply Gmail labels and routing
````

---

## Example Reports

![Queue cleanup after scanning is completed](img/photo_5303173086368702688_w.jpg)

*Figure 4 — Queue cleanup after scan completion, step #1*

![Queue cleanup after scanning is completed](img/photo_5303173086368702687_w.jpg)

*Figure 5 — Queue cleanup after scan completion, step #2*

![Positive report example](img/photo_5303173086368702669_x.jpg)

*Figure 6 — Example of a positive report*

![Report that requires manual verification](img/Снимок%20экрана%202026-06-17%20190427.png)

*Figure 7 — Example of a report requiring verification*

---

## Technologies

* Google Apps Script
* JavaScript
* Python
* PDF parsing libraries
* Gemini API (AI verification stage)
* Gmail API

---

## Purpose

This project was built as a personal learning exercise to study:

* Email security concepts and attack vectors
* Automated PDF analysis techniques
* Rule-based detection systems
* AI-assisted classification workflows
* Integration between Google Apps Script and backend services
* Basic SOC-like decision pipelines

---

## Disclaimer

This project is an educational prototype and is not intended for production use or real-world security enforcement.

```
```
