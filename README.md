# Bulk Interbank Transfer System
**Korean Federation of Community Credit Cooperatives (KFCC) · 2019–2024**

## Overview

This project involved designing and implementing a bulk interbank transfer function for corporate customers at KFCC. The system allowed tellers to upload large batches of transfer requests and process them securely across interbank networks, while maintaining operational clarity and usability for branch staff.

---

## Problem

The existing workflow allowed tellers to upload large batches of transfer requests from Excel files without verifying recipient accounts. This created a significant risk of misdirected transfers caused by minor data-entry errors — a critical concern in high-stakes financial infrastructure.

Two competing challenges had to be solved simultaneously:

1. **Security**: Every recipient account needed to be verified before a transfer could proceed
2. **Usability**: The verification process could not disrupt teller workflows or make the system feel unresponsive

---

## Approach

### 1. Recipient Verification
Integrated a recipient-verification API into the transfer workflow so that each recipient account was validated before any transfer could proceed. Transfers were blocked until verification was confirmed, eliminating the risk of misdirected payments.

### 2. Asynchronous Processing
The external verification service supported only sequential processing, meaning large batches could leave tellers waiting while the terminal appeared frozen and unresponsive.

To address this, I designed an asynchronous workflow that:
- Processed verification responses as they arrived rather than waiting for the full batch
- Displayed real-time progress indicators so tellers could monitor the process without interrupting their work
- Allowed tellers to continue other tasks while verification ran in the background

### 3. Recipient Name Matching and Exception Handling
Added recipient-name matching logic to catch mismatches between account numbers and registered names. Mismatches triggered an explicit review state requiring deliberate teller confirmation before the transfer could proceed.

This ensured that exceptions were never silently passed through — every anomaly required a conscious human decision.

---

## Key Insights

- Security and usability are not opposing goals. With thoughtful design, verification and transparency can reinforce each other
- Asynchronous processing is not just a performance optimization — it is a UX decision that determines whether users trust and adopt a system
- Designing for human decision-making means making exceptions visible, not invisible
- This project deepened my interest in how security workflows can be designed around the cognitive needs of the people operating them

---

## Technical Scope

- Integrated external recipient-verification API into core banking teller terminal
- Designed asynchronous batch processing workflow with real-time progress feedback
- Implemented recipient-name matching and mismatch review states
- Developed exception handling logic requiring explicit teller confirmation
- Operated within interbank financial network infrastructure with strict data integrity requirements

---

## Technologies

`Java` `C` `Oracle SQL` `FEP Systems` `Async Processing` `Core Banking Infrastructure` `Interbank Networks`
