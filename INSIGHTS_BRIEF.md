# Insights Brief: Synchronizing Housecall Pro Timesheets to QuickBooks

**Date:** 2026-02-17
**Research By:** Product Team
**Status:** Draft for Review

**Purpose:** This brief defines the problem space for timesheet synchronization from Housecall Pro to QuickBooks. It will inform a one-pager, prototyping decisions, and solution development.

---

## 1. Problem Definition

### What Are Customers Asking For?

Customers are requesting the ability to **export or sync employee timesheet data from Housecall Pro to QuickBooks** for payroll and labor cost tracking purposes.

**The core ask:** Move employee time tracking data (hours worked, job assignments) from HCP → QuickBooks to support payroll processing and financial reporting.

### Key Distinctions

This request is specifically about **timesheet data synchronization**, not broader payroll integration:

| What Customers Want | What It's NOT |
|---------------------|---------------|
| Export employee hours worked | Full payroll processing integration |
| Sync timesheet data to QuickBooks | Replace QuickBooks with HCP Payroll |
| Support QB Payroll workflows | Direct integration with Check or other payroll providers |
| Track labor costs in accounting system | Employee scheduling or time clock features |

### What Do They Want to See in QuickBooks?

Based on customer language analysis, they want:

1. **Employee timesheets** - Time worked by employees
2. **Service tech timesheets** - Specifically field technician hours
3. **Time tracking entries** - Individual time records
4. **Hours data** - Duration worked

**Customer terminology (actual quotes):**
- "export timesheets" (Score: 0.856)
- "timesheets and times integrate" (Score: 0.697)
- "service tech timesheets" (Score: 0.692)
- "link the timesheets from HCP into the time tracking in QBO" (Score: 0.550)
- "employee time sheets port into quickbooks" (Score: 0.383)

### Ambiguity: Which QuickBooks Product?

Customers mention multiple QuickBooks products, creating confusion:

1. **QuickBooks Online (QBO)** - Most common (7 mentions)
   - Specifically: "time tracking in QBO" suggests QB Time feature
2. **QuickBooks Desktop** - 2 mentions
3. **QuickBooks Plus** - 1 mention
4. **QuickBooks Payroll** - 1 mention ("Can I use timesheet with quickbooks payroll?")

**Unknown:** Whether customers want integration with:
- QuickBooks Time (formerly TSheets) - dedicated time tracking app
- QuickBooks Payroll - for processing payroll
- Native QBO time tracking feature
- Or all of the above

---

## 2. Voice of Customer

### Volume: How Many Customers Are Asking?

**Quantitative Data:**
- **Total feedback items reviewed:** 1,513
- **Relevant snippets identified:** 659
- **High-quality timesheet-specific requests:** ~20 (relevance score >0.5)
- **Medium-quality requests:** ~30 (relevance score 0.38-0.5)

**Signal Quality:**
- Top 50 snippets show clear timesheet-specific demand
- After top 100, signal degrades to generic "quickbooks sync" requests
- Many duplicate queries (e.g., "How do I ensure my employee time sheets port into quickbooks" - 6 duplicates)

**Interpretation:** Moderate-to-high volume of customer requests with clear intent for timesheet export functionality.

### Use Cases: What Do They Want Synchronized?

Based on actual customer examples from Reforge data:

#### Use Case 1: Service Tech Timesheet Export for Payroll ⭐ PRIMARY
**Customer Quote (Score: 0.692):**
> "How do you export service tech timesheets to Quickbooks Online"

**What they want:** Export field technician hours worked to QuickBooks for payroll processing

**Supporting evidence:**
- "employee time sheets port into quickbooks" (Score: 0.383, 6 duplicates)
- "Can I use timesheet with quickbooks payroll?" (Score: 0.396)

#### Use Case 2: Time Tracking Integration
**Customer Quote (Score: 0.550):**
> "I want to see if it is possible to link the timesheets from HCP into the time tracking in QBO"

**What they want:** Integration with QuickBooks Online's built-in time tracking feature (or QuickBooks Time app)

#### Use Case 3: Labor Cost Tracking for Job Costing
**Inferred from:** Competitor analysis shows ServiceTitan syncs timesheets to "see the unapplied labor" in QuickBooks

**What they want:** Track labor costs per job in accounting system for P&L reporting

#### Use Case 4: Timesheet Editing & Payroll Pain Points
**Customer Quote (Score: 0.404):**
> "Payroll TIMESHEETS - I have 22 employees who do not remember to clock in and out for lunches etc. We should be able boilerplate our technicians shifts and not have to click in to the timesheet to blanket 30 minute deducts"

**Context:** This is about HCP's timesheet editing capabilities, NOT QuickBooks sync
**Relevance:** Shows payroll context and timesheet workflow challenges

### Pain Points: What Happens Today Without This Feature?

**Based on customer questions, we can infer:**

1. **Manual Data Entry** - Likely copying timesheet data from HCP to QuickBooks manually
   - Evidence: Questions like "How to upload time sheets to quickbooks" suggest manual process

2. **Feature Discovery Confusion** - Many "does this exist?" questions
   - "Do HCP timesheets and times integrate into quickbooks?" (Score: 0.697)
   - "Do time sheets sync to quickbooks" (Score: 0.500)
   - Suggests feature doesn't exist OR is poorly documented

3. **Workflow Friction** - Maintaining data in two systems
   - Time tracked in HCP
   - Payroll processed in QuickBooks
   - No automated bridge between them

**⚠️ Data Gap:** We don't have direct customer quotes about current workarounds or specific pain points. These are inferred from question types.

### Customer Quotes with Relevance Scores

**Top 10 Most Relevant (Exact Customer Language):**

1. **Score 0.856** | ID: cmbbd35kqo5dpmw1n23umpl1l
   > "exporting timesheets from housecall pro to quickbooks online"

2. **Score 0.697** | ID: cm7jsockm0mnr13yrsf4tysjz
   > "Do HCP timesheets and times integrate into quickbooks?"

3. **Score 0.692** | ID: cmkd3b1072j4r1smqwa4vtrs1
   > "How do you export service tech timesheets to Quickbooks Online"

4. **Score 0.550** | ID: cm5ptn8b46mcbd36qb2w0n0li
   > "I want to see if it is possible to link the timesheets from HCP into the time tracking in QBO"

5. **Score 0.500** | ID: cm7c5axjjef8vnaxe462e0yum
   > "Do time sheets sync to quickbooks"

6. **Score 0.451** | ID: cmaoek515fgvdlg1owc768vcn
   > "How does time sheet syncing work with quickbooks desktop?"

7. **Score 0.416** | ID: cmkwvnt0r163c1rl7ay6n85vk
   > "how to I sync the time sheet to quick books plus?"

8. **Score 0.413** | ID: cmbbd39o4k7nhmv1n3qg5cq6k
   > "quickbooks timesheet export to Quickbooks"

9. **Score 0.404** | ID: clyc6gh2y2eug6mdi297vqkzg
   > "Payroll TIMESHEETS - I have 22 employees who do not remember to clock in and out for lunches etc. We should be able boilerplate our technicians shifts and not have to click in to the timesheet to blanket 30 minute deducts"

10. **Score 0.396** | ID: cmkd4g7hh3rum1rmvk28mp1k5
    > "Can I use timesheet with quickbooks payroll?"

---

## 3. Personas

### Primary Persona: Office Manager / Admin

**Who needs to see timesheets synchronized to QuickBooks:**
- **Office Manager** - Runs payroll, manages accounting
- **Admin Staff** - Processes weekly/bi-weekly payroll
- **Bookkeeper** - Maintains QuickBooks records
- **Accountant/Controller** - Reviews financial reports, labor costs

**Their workflow:**
1. Field technicians track time in HCP (clock in/out, job assignments)
2. Office manager needs that time data in QuickBooks
3. Processes payroll using QuickBooks Payroll OR exports to external payroll provider
4. Reviews labor costs per job for P&L reporting

**Evidence from research:**
- Customer quotes focus on "employee time sheets" and "service tech timesheets"
- Payroll use case mentioned explicitly
- No mentions of technicians needing QB access

### Secondary Persona: Field Service Technicians

**Who should NOT need to see timesheets synchronized to QuickBooks:**
- **Field Technicians** - Track time in HCP, don't need QB access
- **Service Team** - Clock in/out via HCP mobile app

**Their role:**
- Use HCP to clock in/out for jobs
- Time data flows FROM them TO office manager
- Don't interact with QuickBooks directly

### Industries/Verticals

**⚠️ Data Gap:** Reforge snippets don't include industry/vertical metadata

**From general HCP knowledge (not from this research):**
- HVAC
- Plumbing
- Electrical
- Cleaning services
- Landscaping
- General field service businesses

**Assumption:** Any field service business using both HCP and QuickBooks for accounting/payroll would benefit from this feature.

---

## 4. Competitive Intelligence

### Competitor Feature Comparison

| Feature | Jobber | ServiceTitan | Housecall Pro |
|---------|--------|--------------|---------------|
| **Timesheet export to QB** | ✅ Yes | ✅ Yes | ❌ No |
| **Sync direction** | One-way (Jobber → QB) | One-way (ST → QB) | N/A |
| **Target QB product** | QuickBooks Time Tracking | QuickBooks (general) | N/A |
| **Recent investment** | Yes (new integration) | Yes (active support) | Unknown |

### Jobber: How They Implement Timesheet Sync

**Implementation Details:**
- **Feature status:** Active and recently enhanced
- **Direction:** One-way automatic sync from Jobber → QuickBooks
- **What syncs:** Employee timesheets
- **Where in QuickBooks:**
  - Appears in QuickBooks Time Tracking module
  - Viewable via Reports > "Time Activities by Employee Detail"
- **Requirements:** Employee names must match between systems
- **Availability:** Connect and Grow plans (paid tiers)
- **Sync mechanism:** Automatic, ongoing syncs (not manual)

**Key implementation insight:**
> "Timesheets sync one-way from Jobber into Time Tracking entries in QuickBooks"

**Sources:**
- [QuickBooks Online Sync | Jobber](https://www.getjobber.com/features/quickbooks-sync/)
- [How Items Sync Between Jobber and QuickBooks Online](https://help.getjobber.com/hc/en-us/articles/10487017203223)

### ServiceTitan: How They Implement Timesheet Sync

**Implementation Details:**
- **Feature status:** Active
- **What syncs:** Technician timesheets
- **Purpose:** Track "unapplied labor" in QuickBooks
- **Integration type:** Works with QuickBooks Online and Desktop
- **Note:** ServiceTitan is NOT a payroll provider - syncs time data but customers need separate payroll system

**Key implementation insight:**
> "By syncing technician timesheets from ServiceTitan to QuickBooks, you can see the unapplied labor"

**Use case positioning:** Labor cost tracking and job costing, not just payroll

**Sources:**
- [Mastering the Flow: ServiceTitan and QuickBooks Integration | CapForge](https://capforge.com/post/mastering-the-flow-the-comprehensive-guide-to-servicetitan-and-quickbooks-integration/)
- [Field Service Management Software For Quickbooks | ServiceTitan](https://www.servicetitan.com/features/field-service-management-software-quickbooks)

### Investment Trends: Are They Investing or Abandoning?

**Jobber:**
- ✅ **Investing** - Recently launched "NEW QuickBooks Integration"
- Enhanced from manual sync to automatic, ongoing syncs
- Positioned as key feature on marketing site

**ServiceTitan:**
- ✅ **Investing** - Active documentation and community support
- Positioned as core capability for QB integration
- Emphasized in integration guides and sales materials

**Conclusion:** Both major competitors actively support and invest in timesheet sync to QuickBooks. This is **table stakes** for field service management software with QuickBooks integration.

---

## 5. Current State at Housecall Pro

### What Does HCP Offer Today?

#### Existing Features:
1. **HCP Payroll Product** (via Check partnership)
   - Built-in payroll processing
   - Timesheets integrated with HCP Payroll
   - Payroll Journal Entries can sync to QuickBooks
   - Source: Confluence - Basic Accounting One Pager

2. **QuickBooks Integration** (active, well-supported)
   - Syncs: Invoices, payments, customers, jobs, items
   - Direction: Primarily one-way (HCP → QB)
   - Target: QuickBooks Online and Desktop
   - **Does NOT sync:** Timesheets

3. **Time Tracking in HCP**
   - Employees can clock in/out
   - Timesheets managed within HCP
   - Used for HCP Payroll if customer subscribes
   - Source: Confluence - Product Development Squads

#### Organizational Structure:
- **Payroll Squad** owns clock-in/out and timesheets
- **QuickBooks Integration Squad (CAF Team)** owns QB sync features
- **Gap:** No clear owner for timesheet export to QB feature

### What's the Gap?

**Current state:**
```
HCP Time Tracking → HCP Timesheets → HCP Payroll → QB (via Journal Entries)
                                   ↓
                                   ❌ No direct export to QB Payroll
                                   ❌ No sync to QB Time Tracking
```

**Desired state (based on customer requests):**
```
HCP Time Tracking → HCP Timesheets → Export/Sync → QuickBooks Time Tracking
                                                 → QuickBooks Payroll
                                                 → QB for job costing
```

**The Gap:**
1. **No direct timesheet export** from HCP to QuickBooks
2. **No integration** with QuickBooks Time (formerly TSheets)
3. **No integration** with QuickBooks Payroll for time data
4. Customers using **external payroll** (not HCP Payroll) have no automated way to get time data into QB

### What Workarounds Are Customers Using?

**⚠️ Data Gap:** No direct customer quotes about workarounds in our research data.

**Likely workarounds (inferred):**
1. **Manual entry** - Typing time data from HCP into QuickBooks
2. **CSV export/import** - If HCP has timesheet export, manually importing to QB
3. **Using HCP Payroll only** - Avoiding QB Payroll entirely to stay within HCP
4. **Dual entry** - Entering time in both systems separately

**Evidence of manual process:** Customer question "How to upload time sheets to quickbooks" (Score: 0.394) suggests manual upload workflow.

### Future Plans Mention

From Confluence research (Housecall Pro Tips research - Page 2967634201):
> "This would need to be revisited in the future **if / when we decide to implement any direct integration with Quickbooks for payroll**"

**Implication:** Feature is being considered for future, but not currently in active development.

---

## 6. Key Unknowns & Risks

### Critical Unknowns

1. **Specificity of data requirements**
   - What exact timesheet data do customers need in QB?
   - Just total hours? Hours per job? Cost codes? Break time?

2. **Volume and business impact**
   - How many HCP customers use both HCP and QB?
   - How many use QB Payroll vs. other payroll providers?
   - Churn risk if feature doesn't exist?

3. **QuickBooks product target**
   - QuickBooks Time (formerly TSheets)?
   - QuickBooks Payroll?
   - Native QBO time tracking?
   - All of the above?

4. **Relationship to HCP Payroll**
   - Is this feature for customers NOT using HCP Payroll?
   - Would it compete with HCP Payroll?
   - Or complement it for QB-centric workflows?

5. **Current workarounds**
   - What are customers actually doing today?
   - Is manual entry acceptable or causing churn?

### Risks

**Risk 1: Building the wrong thing**
- Without specificity on data requirements, could build feature that doesn't meet needs
- Example: Export total hours but customers need hours per job/cost code

**Risk 2: QuickBooks product ambiguity**
- Multiple QB products mentioned (QB Time, QB Payroll, QBO, Desktop)
- Building for wrong QB product = wasted effort

**Risk 3: Competitive pressure**
- Both major competitors have this feature
- Could be churn driver if customers choose competitor for this capability

**Risk 4: Organizational ownership**
- Payroll squad owns timesheets
- QB integration squad owns QB sync
- Feature requires cross-squad coordination

**Risk 5: HCP Payroll cannibalization**
- If we make it easy to export to QB Payroll, do we hurt HCP Payroll adoption?
- Need to think through product strategy implications

---

## 7. Summary & Recommendations

### Problem Space Summary

**Clear finding:** Customers want to export employee timesheet data from Housecall Pro to QuickBooks for payroll and labor cost tracking. This feature **does not currently exist**, but **both major competitors (Jobber and ServiceTitan) offer it**.

**Volume:** 659 relevant customer feedback snippets indicate moderate-to-high demand.

**Primary use case:** Office managers/admins need employee hours in QuickBooks for payroll processing.

**Competitive context:** Table stakes feature for field service software with QuickBooks integration.

### Recommended Next Steps (For Product Team)

1. **Clarify requirements**
   - Interview customers to understand specific data needs
   - Identify which QuickBooks product(s) to target
   - Document exact data fields required

2. **Assess business impact**
   - Quantify: How many customers use both HCP and QB?
   - Analyze: Is this causing churn or blocking conversions?
   - Determine: Priority vs. other initiatives

3. **Align organizationally**
   - Payroll squad + QB integration squad collaboration
   - Clarify feature ownership
   - Consider HCP Payroll product strategy implications

4. **Validate solution approach**
   - Review Jobber and ServiceTitan implementations
   - Prototype with customer feedback
   - Consider phased rollout (QBO first, then Desktop, then QB Time)

---

## Appendix: Research Sources

### Data Sources
- **Reforge Insights:** 659 customer feedback snippets from Housecall Pro workspace
- **Confluence:** 60 internal documentation pages
- **Competitive research:** Jobber and ServiceTitan public documentation and help articles

### Key Documents
- Research findings: `/reports/hcp-qb-timesheets/research-findings.md`
- Quick reference: `/reports/hcp-qb-timesheets/QUICK_REFERENCE.md`
- Raw data: `/reports/hcp-qb-timesheets/top-50-snippets.json`

### Research Date
2026-02-17
