# 📋 PRO-DENT CLUB: TEAM IMPLEMENTATION S.O.P & EXECUTION PLAN
**Client:** Eric Tang (Upwork)  
**Budget Locked:** $600  
**Final Deadline:** Tuesday Morning (Canada/US EST) — Internal Completion: Monday Night PKT  
**Target Goal:** 100% Tested, Verified, and Ready-to-Send Automation

---

## 📌 PROJECT OVERVIEW & SCOPE BREAKDOWN

Hamare paas 4 core modules hain:
1. **Module 1:** ADP Partnership Launch Email Template (HTML)
2. **Module 2:** Dynamic Member Savings Email Template (HTML with GHL Merge Tags)
3. **Module 3:** GoHighLevel (GHL) Custom Fields, Trigger & Automated Workflow
4. **Module 4:** Wix Integration Audit & Onboarding Nurture Sequences Check

---

## 🚀 MODULE 1: ADP PARTNERSHIP LAUNCH EMAIL (HTML)

### 1.1 Objective & Brand Context
- **Partner:** ADP Canada (`https://www.adp.ca/en.aspx`)
- **Product:** *Workforce on The Go* (Automated Payroll Administration for Dental Practices)
- **Exclusive Offer:** **40% OFF** their payroll program for Pro-Dent Club members
- **Direct Contact/CTA:** Forward email / reach out to `harkarn.grewal@ADP.com`
- **Design Note:** Staples announcement se inspired ho sakta hai lekin copy-paste nahi hona chahiye. Distinct ADP aesthetic honi chahiye.

### 1.2 Design & Tech Specs
- **Color Palette:**
  - ADP Signature Red: `#D0271D` or `#E31837`
  - Deep Dark Background: `#0F172A` / `#121317` (similar to Staples dark container)
  - Card/Body Background: Light Cream `#F8FAFC` or `#F2F0ED` (to preserve deliverability and readability)
  - Text Primary: `#1E293B`, Secondary: `#64748B`
- **Email Structure:**
  1. **Preheader:** *"Save 40% on ADP's Workforce on The Go — exclusive for Pro-Dent Club practices."*
  2. **Co-branded Header:** Pro-Dent Club logo + "×" + ADP Logo.
  3. **Hero Section:**
     - Bold Headline: *"Simplify Your Practice Payroll. Enjoy Exclusive 40% Member Savings."*
     - Value proposition: Dental staff payroll, CRA remittances, direct deposit, and year-end T4s made effortless.
  4. **The 40% Discount Highlight Card:**
     - Red/Dark border with large "40% OFF" badge.
     - Feature checklist (Automatic tax filing, ROE automation, mobile employee app).
  5. **Call-To-Action (CTA):**
     - Button: `[ Forward to Harkarn @ ADP to Claim Discount ]`
     - Mailto Link: 
       `mailto:harkarn.grewal@ADP.com?subject=Pro-Dent%20Club%20Member%20-%2040%25%20ADP%20Payroll%20Discount&body=Hi%20Harkarn%2C%20I%20am%20a%20Pro-Dent%20Club%20member%20interested%20in%20activating%20the%2040%25%20discount%20on%20ADP%20Workforce%20on%20The%20Go.`
     - Instructional note below button: *"Alternatively, simply forward this email directly to harkarn.grewal@ADP.com with your practice name."*
  6. **Footer:** Standard Pro-Dent Club compliance & unsubscribe links.

---

## 🚀 MODULE 2: DYNAMIC MEMBER SAVINGS EMAIL (HTML + GHL TAGS)

### 2.1 Objective
Alice (calling rep) dental practice se baat karegi, unki estimated savings figure calculate karegi, aur GHL profile me enter karegi. Ye email automatically dynamic savings amount + 3 vendors ke onboarding links ke sath practice ko send hogi.

### 2.2 Dynamic Merge Fields Required in Code
- Practice Name: `{{contact.practice_name}}` (Fallback: `{{contact.company_name}}` ya *"Your Practice"*)
- Contact Name: `{{contact.first_name}}`
- Rep Savings Estimate: `{{contact.estimated_savings}}` (e.g. `$2,450`)

### 2.3 Email Layout & Content Sections
1. **Preheader:** *"Your customized savings estimate + access your Pro-Dent vendor perks."*
2. **Personalized Header & Intro:**
   - *"Hi {{contact.first_name}}, following our recent call with {{contact.practice_name}}, here is your tailored cost reduction overview."*
3. **Hero Savings Badge Box (High Impact):**
   - High-contrast card (Navy `#1B2A4A` or Dark Emerald with bold cyan/gold accent):
   - Title: `YOUR ESTIMATED ANNUAL PRACTICE SAVINGS`
   - Dynamic Tag: **`${{contact.estimated_savings}}`**
   - Subtext: *"Estimated across sundries, payment processing, and core clinic operations."*
4. **The 3 Featured Vendors Showcase (3 Clean Cards / Stacks):**
   - **Vendor A: K-Dental**
     - Description: Canada’s premier dental supply partner (sundries, handpieces, equipment).
     - Button: `[ Complete K-Dental Onboarding Form ]` (Same link as existing onboarding email).
   - **Vendor B: Snap**
     - Description: Patient financing & flexible payment solutions to boost case acceptance.
     - Button: `[ Activate Snap Financing ]`.
   - **Vendor C: Staples Professional**
     - Description: Exclusive member rates on office, sanitation, and breakroom essentials.
     - Button: `[ Register Your Staples Account ]`.
5. **Interactive FAQ Section:**
   - *Q: How do these discounts apply?*
   - *Q: Is there any long-term obligation or membership fee?*
   - *Q: What if I already have an existing account with these vendors?*
6. **Support & Sign-off:**
   - *"Questions? Reply directly to this email or speak with your dedicated rep."*

---

## ⚙️ MODULE 3: GOHIGHLEVEL (GHL) AUTOMATION & FIELD ARCHITECTURE

*(Team member handling GHL should follow this exact click-by-click flow)*

### 3.1 Step 1: Create Custom Fields in GHL
Location: **Settings -> Custom Fields -> Add Custom Field**
1. **Field 1: Practice Name**
   - Type: `Single Line Text`
   - Label: `Practice Name`
   - Group: Contact / General Info
2. **Field 2: Estimated Savings**
   - Type: `Monetary` (or `Single Line Text`)
   - Label: `Estimated Savings`
   - Group: Additional Info
3. **Field 3: Trigger Checkbox**
   - Type: `Checkbox (Single Option)`
   - Label: `Send Savings Estimate Email`
   - Option Value: `Send Email` (or `Checked`)

### 3.2 Step 2: Build the Workflow
Location: **Automation -> Workflows -> Create Workflow (Start from Scratch)**
- **Workflow Name:** `[Trigger] Member Personalized Savings Email Automation`
- **Trigger:**
  - Select Trigger: `Contact Changed`
  - Filter: Select Custom Field `Send Savings Estimate Email`
  - Condition: `Has Changed` AND `is equal to Checked / Send Email`
- **Action 1: Send Email**
  - From Name: `Pro-Dent Club` (or `{{user.name}}`)
  - From Email: Verified Pro-Dent sending address
  - Subject Line: `Your Practice Savings Breakdown & Vendor Setup — {{contact.practice_name}}`
  - Template: Select the HTML template built in Module 2
- **Action 2: Reset Checkbox Field (Crucial Step!)**
  - Action Type: `Update Contact Field`
  - Field: `Send Savings Estimate Email`
  - Value: `Unchecked / False`
  - *Why:* Taake rep agar future me dubara email bhejna chahe toh box re-check karne se trigger dobara fire ho sake.
- **Action 3: Add Tag / Internal Notification**
  - Action: `Add Contact Tag` -> Tag Name: `savings-email-sent`
  - Optional: `Internal Notification` to Alice confirming the email was successfully sent.
- **Settings:**
  - Turn ON: **Allow Re-entry** (taake dubara bhej saken agar needed ho).
  - Click **Publish** and **Save**.

### 3.3 Step 3: Rep (Alice) Operational Flow Verification
Test contact bana kar verify karein:
1. Contact create karein: `Test Practice`, Name: `Dr. Smith`.
2. Alice field me likhegi: `$1,850`.
3. Checkbox `Send Savings Estimate Email` ko tick karke Save karegi.
4. Inbox me check karein ke email foran receive hui aur `$1,850` aur `Test Practice` sahi replace hue.

---

## 🔍 MODULE 4: WIX INTEGRATION & ONBOARDING FLOW AUDIT

Eric ne explicitly kaha tha: *"if theres anything we havent done yet like the wix integration, or connecting the 3 onboarding emails, to the flow, or the vendor spreadsheet, lets finish that ASAP"*

### 4.1 Wix to GHL Form & Webhook Check
1. Wix dashboard me jayein -> Automations / Forms.
2. Verify karein ke jab naya member sign up kare toh webhook GHL me trigger ho raha hai ya direct app integration se contact create ho raha hai.
3. Test submission karein aur check karein ke contact GHL me `New Member` tag ke sath create ho raha hai.

### 4.2 3 Onboarding Emails Flow Audit
1. GHL Workflow me jayein jahan new members ki onboarding chalti hai.
2. Check karein ke teenon emails:
   - Email 1: Welcome & Setup (`onboarding-template-onev1.html`)
   - Email 2: Vendor Deep Dive (`onboarding-template-tow-v1.html`)
   - Email 3: Perks & Reminders (`onboarding-template-three.html`)
   Proper time delays (e.g., Immediate, Wait 2 Days, Wait 4 Days) ke sath linked hain ya nahi.

### 4.3 Vendor Spreadsheet Sync
1. Check karein ke Google Sheets action active hai: Jab member register hota hai toh kya Vendor Spreadsheet me row append ho rahi hai?
2. Agar Zapier ya Make.com use ho raha hai, check karein koi error ya disconnected account toh nahi hai.

---

## ⏱️ TEAM TIMELINE & DELEGATION SCHEDULE (MONDAY)

| Time (PKT) | Responsibility | Deliverable |
|---|---|---|
| **09:30 AM - 12:30 PM** | Developer / Designer | Build ADP Launch HTML Template + Dynamic Savings HTML Template |
| **01:30 PM - 03:00 PM** | GHL Specialist | Create Custom Fields, Checkbox Trigger, Workflow & Test Run |
| **03:00 PM - 04:30 PM** | QA / Tech Lead | Wix Webhook Audit, 3 Onboarding Emails check, Vendor Sheet Sync |
| **05:00 PM PKT** | Project Lead (Sardar) | Live Test Email Send + Loom/Preview links ready for Eric |
| **08:00 PM PKT / 11:00 AM EDT** | Client Review Window | Eric review karega, feedback/minor tweaks apply honge |
| **Tuesday Early AM EDT** | Final Handover | 100% Locked, Tested, and Live in Production |

---

## ✅ FINAL QUALITY ASSURANCE CHECKLIST (BEFORE SENDING TO ERIC)
- [ ] ADP Template displays perfectly in Apple Mail, Gmail, and Outlook Dark Mode.
- [ ] ADP CTA `mailto` subject line and Harkarn's email address are 100% accurate.
- [ ] Dynamic merge tags in Savings Email have fallbacks (agar savings khali ho toh crash na kare).
- [ ] Checkbox workflow resets properly after sending.
- [ ] All 3 vendor links (K-Dental, Snap, Staples) work properly and point to live onboarding forms.
- [ ] Wix forms create leads in GHL without errors.
