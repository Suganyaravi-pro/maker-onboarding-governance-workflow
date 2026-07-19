# 🔐 Maker Onboarding & Governance Workflow

## Overview
A Power Automate workflow that automates the Maker onboarding and approval process, enforcing mandatory assessment completion before users can request Advanced Citizen Developer access.

## Problem
Previously, there was no governance process in place for granting Advanced Citizen Developer access — no assessment existed to validate a maker's readiness before they were given access. This created a gap in compliance and increased the risk of ungoverned citizen development.

## What I Built
I designed and built a Power Automate workflow to automate the Maker onboarding and approval process, from assessment submission through to certificate issuance and access approval.

## Process Flow
1. **Entry point:**
   - **Scenario A:** the user clicks the assessment link from the **PowerUp 360° portal** (the Power Apps Canvas enablement hub built in [Power Platform Enablement Hub](https://github.com/Suganyaravi-pro/power-platform-enablement-hub))
   - **Scenario B:** if a user goes directly to the MyAccess portal and attempts to raise an access request without completing the assessment, MyAccess blocks the request and shows a popup (built by the MyAccess team) prompting the user to complete the assessment first before they can proceed
2. **Assessment submission** — the user completes the assessment via Microsoft Forms
3. **Score evaluation** — my workflow evaluates the score against the required threshold
   - If the score is **below the threshold**, the user is automatically notified via email to retake the assessment
   - If the score **meets the threshold**, the workflow proceeds to certification and role request
4. **Certificate generation** — on passing, the flow automatically:
   - Records the user's assessment completion details in SharePoint
   - Retrieves the certificate template file content from SharePoint
   - Composes the data to populate the template
   - Populates the Microsoft Word certificate template with the user's details
   - Creates the Word file
   - Converts the Word file to PDF
   - Creates the PDF file
   - Deletes the intermediate Word file
   - Sends the completed "Maker Certificate" via outlook to the user
5. **Role request to MyAccess** — I built the integration to authenticate (Get OAuth Token, Parse JSON) and send a role request to MyAccess, populating the user's details on their end
6. **Two-stage approval:**
   - **Team Lead approval** — validates business justification and need for access
   - **MyAccess approval** — validates technical/access-governance compliance
7. **Approver notification** — designated approvers and users are notified via Outlook; once both approval stages are complete, the user is notified that their access request has been granted

## Impact
- Enforced mandatory assessment completion before granting Advanced Citizen Developer access
- Removed manual validation steps, reducing onboarding turnaround time
- Automated certificate generation and delivery, eliminating manual document handling
- Streamlined approver notifications through Teams and Outlook integration
- Improved compliance with organizational governance policies

## Tech Used
`Power Automate` `Microsoft Forms` `SharePoint` `MyAccess` `Microsoft Word` `Outlook` `JSON` `OAuth`

---
*Note: This repository is a write-up of a project built during my professional role. Actual source code and company data are confidential and not included here.*
