# Research Findings: Synchronizing Housecall Pro Timesheets to QuickBooks

**Research Date:** 2026-02-17
**Topic:** Understanding customer needs for timesheet synchronization from HCP to QuickBooks

---

## Research Progress

### Phase 1: Data Collection (In Progress)
- [x] Reforge customer feedback analysis - VOLUME CHECK COMPLETE
- [ ] Deep analysis of Reforge data (pending user decision)
- [ ] Confluence prior research check
- [ ] Competitive intelligence (Jobber, ServiceTitan)

---

## 1. REFORGE DATA - VOLUME ANALYSIS

**Search Query:** "Feedback about timesheets synchronization to QuickBooks"
**Source:** Reforge Insights - Housecall Pro workspace
**Date:** 2026-02-17

### Volume Metrics
- **Total feedback items checked:** 1,513
- **Relevant snippets found:** 659 snippets
- **Relevance:** QuickBooks project area + "timesheets synchronization" filter
- **Relevance Score Range:** 0.856 (highest) to lower scores

### Top 20 Snippets (by relevance score)

**High Confidence (>0.65 score):**
1. **Score 0.856** - "exporting timesheets from housecall pro to quickbooks online"
2. **Score 0.697** - "Do HCP timesheets and times integrate into quickbooks?"
3. **Score 0.692** - "How do you export service tech timesheets to Quickbooks Online"

**Medium-High Confidence (0.5-0.65 score):**
4. **Score 0.550** - "I want to see if it is possible to link the timesheets from HCP into the time tracking in QBO"
5. **Score 0.500** - "Do time sheets sync to quickbooks"

**Medium Confidence (0.4-0.5 score):**
6. **Score 0.451** - "How does time sheet syncing work with quickbooks desktop?"
7. **Score 0.416** - "how to I sync the time sheet to quick books plus?"
8. **Score 0.413** - "quickbooks timesheet export to Quickbooks"
9. **Score 0.408** - "quickbook sync"
10. **Score 0.404** - Payroll/Timesheets - "I have 22 employees who do not remember to clock in and out for lunches etc. We should be able boilerplate our technicians shifts and not have to click in to the timesheet to blanket 30 minute deducts"

**Note:** Many lower-scored results (~0.40) are generic "quickbooks sync" or "sync projects with quickbooks" - may not be specifically about timesheets.

### Initial Observations from Top 30 Sample

**High-Value Snippets (Score >0.5):**
- Snippet 1 (0.856): "exporting timesheets from housecall pro to quickbooks online"
- Snippet 2 (0.697): "Do HCP timesheets and times integrate into quickbooks?"
- Snippet 3 (0.692): "How do you export service tech timesheets to Quickbooks Online"
- Snippet 4 (0.550): "I want to see if it is possible to link the timesheets from HCP into the time tracking in QBO"
- Snippet 5 (0.500): "Do time sheets sync to quickbooks"

**Medium-Value Snippets (Score 0.4-0.5):**
- Snippet 10 (0.404): Payroll use case - "I have 22 employees who do not remember to clock in and out for lunches etc. We should be able boilerplate our technicians shifts and not have to click in to the timesheet to blanket 30 minute deducts"
- Snippet 19 (0.396): "Can I use timesheet with quickbooks payroll?"

**Low-Value Snippets (Score <0.4):**
- Many generic "quickbooks sync" or "sync with quickbooks" requests (not timesheet-specific)

**Signal Quality Assessment:**
- ✓ Top ~50-100 results likely timesheet-specific
- ⚠️ Lower-scored results diluted with generic QB sync requests
- ✓ Clear themes emerging: export, integration, payroll use case
- ⚠️ Most snippets are short queries - need to check if longer content exists

**Key Questions:**
1. Are customers asking "does this exist?" vs "how do I use it?"
2. Distinction between: timesheet sync vs. time tracking vs. payroll integration
3. QuickBooks Online vs. Desktop vs. QuickBooks Payroll vs. QuickBooks Time

---

## 2. DEEP ANALYSIS - TOP 50 SNIPPETS

**Dataset:** Top 50 snippets by relevance score (0.856 to 0.382)
**Source File:** `/reports/hcp-qb-timesheets/top-50-snippets.json`

### Key Findings

#### A. Customer Intent - Two Distinct Question Types

**1. Discovery Questions (16 snippets) - "Does this feature exist?"**
- "Do HCP timesheets and times integrate into quickbooks?" (Score: 0.697)
- "Do time sheets sync to quickbooks" (Score: 0.500)
- "Can I use timesheet with quickbooks payroll?" (Score: 0.396)
- **Insight:** Customers uncertain if feature exists at all

**2. How-To Questions (12 snippets) - "How do I use this?"**
- "How do you export service tech timesheets to Quickbooks Online" (Score: 0.692)
- "How does time sheet syncing work with quickbooks desktop?" (Score: 0.451)
- "How to upload time sheets to quickbooks" (Score: 0.394)
- "How do I ensure my employee time sheets port into quickbooks" (Score: 0.383, 6 duplicates)
- **Insight:** Suggests feature may exist but customers can't find it or it's unclear

**3. Generic Sync Requests (22 snippets)**
- "quickbooks sync" / "sync with quickbooks" (many duplicates)
- **Insight:** Low signal - not timesheet-specific

#### B. Terminology Analysis - What Customers Call It

Customers use **5 different verbs** to describe the same need:
1. **"Export"** (4 mentions) - Most common: "exporting timesheets from housecall pro to quickbooks online"
2. **"Sync"** (8 mentions) - "Do time sheets sync to quickbooks"
3. **"Integrate"** (2 mentions) - "Do HCP timesheets and times integrate into quickbooks?"
4. **"Link"** (1 mention) - "link the timesheets from HCP into the time tracking in QBO"
5. **"Port"** (6 mentions) - "How do I ensure my employee time sheets port into quickbooks"
6. **"Upload"** (1 mention) - "How to upload time sheets to quickbooks"

**Insight:** No standardized terminology - customers don't know what to call this feature

#### C. QuickBooks Product Variants Mentioned

1. **QuickBooks Online (QBO)** - 7 mentions (most common)
   - "time tracking in QBO" - suggests QB Time integration
2. **QuickBooks Desktop** - 2 mentions
3. **QuickBooks Plus** - 1 mention
4. **QuickBooks Payroll** - 1 mention
5. Generic "QuickBooks" - majority of mentions

**Insight:** QBO is primary target, but Desktop users also asking

#### D. Use Cases Identified

**Use Case 1: Service Tech Timesheet Export for Payroll** (HIGH CONFIDENCE)
- "How do you export service tech timesheets to Quickbooks Online" (Score: 0.692)
- "How do I ensure my employee time sheets port into quickbooks" (Score: 0.383)
- **Who:** Office managers/admin running payroll
- **What:** Export employee time data from HCP to QB for payroll processing

**Use Case 2: Time Tracking Integration** (MEDIUM CONFIDENCE)
- "I want to see if it is possible to link the timesheets from HCP into the time tracking in QBO" (Score: 0.550)
- **What:** Specifically mentions "time tracking in QBO" - likely referring to QuickBooks Time (formerly TSheets)
- **Distinction:** This is integration with QB Time app, NOT just exporting to QB

**Use Case 3: Payroll Pain Points** (HIGH CONFIDENCE)
- Score 0.404: "Payroll TIMESHEETS - I have 22 employees who do not remember to clock in and out for lunches etc. We should be able boilerplate our technicians shifts and not have to click in to the timesheet to blanket 30 minute deducts"
- **Pain:** Manual timesheet editing for lunch breaks
- **Context:** Shows current HCP timesheet limitations, not QB sync issue

**Use Case 4: Multi-Day Job Tracking** (LOW CONFIDENCE - needs validation)
- Score 0.393: "[ORGANIZATION] doesn't sync both ways with [ORGANIZATION] online, and there is time tracking difficulty with multiple day jobs across payroll periods."
- **Pain:** Jobs spanning multiple days/payroll periods create tracking issues
- **Question:** Is this about invoice sync or timesheet sync? Unclear.

#### E. Pain Points & Workarounds

**Pain Point 1: Feature Discovery**
- High volume of "does this exist?" questions
- Suggests feature is either:
  a) Doesn't exist, OR
  b) Exists but hard to find/poorly documented

**Pain Point 2: One-Way Sync Issue** (if sync exists)
- "doesn't sync both ways" (Score: 0.393)
- **Implication:** If sync exists, it's one-way only (HCP → QB)

**Pain Point 3: Current Workarounds**
- No explicit workarounds mentioned in these snippets
- Need to investigate: Are customers manually entering time data?

#### F. Personas (Inferred)

**Primary Persona: Office Manager / Admin**
- Runs payroll using QuickBooks
- Needs employee timesheet data from HCP
- Currently may be manually entering time data

**Secondary Persona: Service Technicians**
- Clock in/out in HCP
- Not mentioned as needing QB access
- Time data flows FROM them TO office manager

#### G. Data Quality Notes

**High-Quality Signals:**
- Top 10 snippets (score >0.4) are timesheet-specific
- Clear pattern: export/sync timesheets TO QuickBooks

**Low-Quality Signals:**
- Many generic "quickbooks sync" requests (score <0.4)
- Lots of duplicates (same query from multiple customers)
- Most snippets are SHORT - just customer queries without additional context

**Missing Information:**
- No customer quotes about WHY they need this
- No details about current workarounds
- No industry/vertical data in these snippets
- No specifics about WHAT timesheet data they want (hours only? job codes? cost codes?)

### Summary: Top 50 Analysis

**Volume:** 50 snippets analyzed
- **~20 high-value** timesheet-specific snippets
- **~30 low-value** generic QB sync requests

**Primary Finding:** Clear demand for exporting/syncing HCP timesheet data TO QuickBooks (primarily QBO) for payroll purposes.

**Key Question Still Unanswered:**
1. What SPECIFIC timesheet data do customers want in QuickBooks? (Total hours? Job assignments? Cost codes? Break time?)
2. Does this feature exist today? If yes, why so many "does this exist?" questions?
3. What are customers doing today as workarounds?

---

## 3. CONFLUENCE PRIOR RESEARCH

**Search Queries:**
1. "timesheets QuickBooks integration sync"
2. "QuickBooks Time TSheets payroll"

**Total Results:** 60 Confluence pages reviewed

### Key Findings from Internal Documentation

#### A. Organizational Structure (Source: Product Development Squads - Page 699531721)
- **Critical Finding:** "clock-in/out and timesheets which the payroll squad owns"
- **Implication:** Timesheets are owned by PAYROLL squad, NOT QuickBooks integration squad
- **Gap:** QuickBooks integration team doesn't own timesheet sync functionality

#### B. Prior Customer Research (Source: Quickbooks Users Research - Page 2734752244)
- "Using Quickbooks for Payroll was directly mentioned few times by Pros in the survey"
- Suggests payroll integration with QB could increase "stickiness" of QB integration
- **Evidence:** Customers want payroll-related QuickBooks integration

#### C. Future Plans Mention (Source: Housecall Pro Tips research - Page 2967634201)
- "This would need to be revisited in the future if / when we decide to implement any direct integration with Quickbooks for payroll"
- **Implication:** No current direct QB payroll integration exists
- **Status:** Feature is being considered for future, not currently implemented

#### D. Basic Accounting Product (Source: Basic Accounting One Pager - Page 3160801879)
- "[As a HCP Payroll attached Pro] when I process payroll, I want payroll Journal Entries created automatically and instantly"
- Focus on HCP's own payroll product, not QB Payroll integration

#### E. Commission Tracking (Source: Commission List View One Pager - Page 3020587009)
- Mentions "QuickBooks Payroll enables businesses to track commissions"
- Reference to QB Payroll as competitor/alternative

#### F. Time Tracking & Payroll Integration (Source: Integrating PTO into Time Tracking and Payroll - Page 2254177048)
- "We want to have the Time Off data available in Timesheets (and in the future in Payroll as well)"
- Mentions passing PTO hours to Check (HCP's payroll provider)
- **No mention of QuickBooks integration for timesheets**

#### G. Payroll Feedback Report (Source: Monterey feedback - Page 2643757518)
- "users are asking for easier ways to sync time entries with payroll"
- **No specific mention of QuickBooks** - appears to be about HCP's own payroll

### Confluence Summary

**What We Found:**
- Extensive documentation about QuickBooks integration for invoices, jobs, payments
- Clear organizational ownership: Payroll squad owns timesheets
- References to QuickBooks Payroll as separate product

**What We Did NOT Find:**
- No PRDs or documentation about timesheet sync to QuickBooks
- No existing feature for exporting timesheets to QB
- No plans currently in flight for this feature

**Conclusion:** Based on internal docs, timesheet export to QuickBooks does NOT currently exist as a feature.

---

## 4. COMPETITIVE INTELLIGENCE

### A. Jobber - QuickBooks Timesheet Integration

**Feature Status:** ✅ **EXISTS AND ACTIVELY SUPPORTED**

**Implementation Details:**
- **Direction:** One-way sync from Jobber → QuickBooks Time Tracking
- **What syncs:** Employee timesheets
- **Where it appears:** QuickBooks Reports > "Time Activities by Employee Detail"
- **Requirements:** Employee names must match between systems
- **Plan availability:** Connect and Grow plans
- **Sync type:** Automatic, ongoing syncs (new integration)

**Key Quotes from Jobber Documentation:**
- "Timesheets sync one-way from Jobber into Time Tracking entries in QuickBooks"
- "Past invoices, payments, payouts, and timesheets can be brought into QuickBooks from Jobber"

**Sources:**
- [QuickBooks Online Sync | Jobber](https://www.getjobber.com/features/quickbooks-sync/)
- [How Items Sync Between Jobber and QuickBooks Online](https://help.getjobber.com/hc/en-us/articles/10487017203223)
- [Timesheet Software with QuickBooks Online Integration | WeWorked](https://www.weworked.com/quickbooks-invoices-timesheets)

### B. ServiceTitan - QuickBooks Timesheet Integration

**Feature Status:** ✅ **EXISTS**

**Implementation Details:**
- **What syncs:** Technician timesheets to QuickBooks
- **Purpose:** View "unapplied labor" in QuickBooks
- **Payroll Note:** ServiceTitan is NOT a full payroll solution
- **Integration:** Works with QuickBooks Online and Desktop
- **Additional requirement:** Separate payroll provider needed (Gusto, ADP, QB Payroll)

**Key Quotes:**
- "By syncing technician timesheets from ServiceTitan to QuickBooks, you can see the unapplied labor"
- "ServiceTitan offers time tracking and timesheet management that integrates with payroll systems, but it is not a full payroll solution"

**Sources:**
- [Mastering the Flow: ServiceTitan and QuickBooks Integration | CapForge](https://capforge.com/post/mastering-the-flow-the-comprehensive-guide-to-servicetitan-and-quickbooks-integration/)
- [Field Service Management Software For Quickbooks | ServiceTitan](https://www.servicetitan.com/features/field-service-management-software-quickbooks)
- [Timesheets and Payroll - ServiceTitan Community](https://community.servicetitan.com/t5/Timesheets-and-Payroll/bd-p/timesheets_payroll)

### Competitive Analysis Summary

| Feature | Jobber | ServiceTitan | Housecall Pro |
|---------|--------|-------------|---------------|
| **Timesheet export to QB** | ✅ Yes | ✅ Yes | ❌ No (based on research) |
| **Sync direction** | One-way (Jobber → QB) | One-way (ST → QB) | N/A |
| **What syncs** | Employee timesheets | Technician timesheets | N/A |
| **Where in QB** | Time Tracking / Reports | Shows unapplied labor | N/A |
| **Current investment** | Active (new integration launched) | Active | Unknown |

**Competitive Insight:**
- **BOTH major competitors offer timesheet sync to QuickBooks**
- This is NOT a niche feature - it's table stakes for field service software with QB integration
- Jobber recently invested in a "NEW QuickBooks Integration" that includes timesheet sync
- ServiceTitan positions it as a way to track labor costs in QB

---

## 5. RESEARCH SUMMARY & GAPS

### What We Learned

**From Reforge (659 snippets):**
- Clear customer demand for timesheet export/sync to QuickBooks
- Mix of discovery ("does this exist?") and how-to questions
- Primary use case: Payroll processing
- Target: QuickBooks Online primarily

**From Confluence (60 pages):**
- Feature does NOT currently exist in HCP
- Timesheets owned by Payroll squad, not QB integration squad
- No active PRDs or plans found for this feature
- References to potential future QB payroll integration

**From Competitors:**
- Jobber: Active feature, recently enhanced
- ServiceTitan: Active feature
- Both position it for labor cost tracking and payroll

### Critical Gaps in Data

**Gap 1: Specificity of Customer Needs**
- ❓ What SPECIFIC timesheet data do customers want in QB?
  - Just total hours?
  - Hours per job/project?
  - Cost codes or service items?
  - Break time deductions?
  - Overtime calculations?

**Gap 2: Current Workarounds**
- ❓ What are customers doing today?
  - Manual entry into QB?
  - Using third-party tools?
  - Exporting CSV and importing?
  - Not using QB for payroll at all?

**Gap 3: QuickBooks Product Confusion**
- ❓ Which QB product do customers actually want?
  - QuickBooks Time (formerly TSheets) - dedicated time tracking app?
  - QuickBooks Payroll - for payroll processing?
  - QuickBooks Online general time tracking feature?
  - QuickBooks Desktop?

**Gap 4: Volume & Business Impact**
- ❓ How many customers are affected?
  - Total HCP customers using QB integration
  - % using HCP Payroll vs. external payroll
  - % using QB Payroll specifically
  - Churn risk if feature doesn't exist?

**Gap 5: Integration with HCP Payroll**
- ❓ How does this relate to HCP's own payroll product?
  - Do customers using HCP Payroll still need QB export?
  - Is this only for customers NOT using HCP Payroll?
  - Competitive threat vs. complementary feature?

### Next Steps Needed (for user decision)

Before creating insights brief, we need to decide:
1. **Dig deeper into gaps?** More targeted Reforge searches for specific data needs?
2. **Talk to customers?** Interview customers who asked about this feature?
3. **Talk to internal teams?** Payroll squad, QB integration squad, CS team?
4. **Proceed with what we have?** Create brief based on current findings?

---

## Findings

_Research complete. Ready for user review and brief creation._
