# Options Doc: Timesheets to QuickBooks Online Sync

**Document Status:** In Progress
**Related One-Pager:** [Timesheets to QuickBooks Online Sync](https://housecall.atlassian.net/wiki/x/_IC15Q)

## Customer Problem

Office managers and admins who use both Housecall Pro and QuickBooks Online need to manually transfer employee timesheet data between systems for payroll processing—affecting ~14,000 HCP organizations. This manual workflow creates errors, wastes time (30-60+ minutes per payroll cycle), and contributes to 6.62% churn in our highest-value customer segment.

## Technical Problem

**Integration complexity:**
- QuickBooks offers multiple time tracking products (QBO native time tracking, QuickBooks Time/TSheets app, QB Payroll)
- Employee matching between systems (names must match exactly)
- Data format mapping (HCP timesheet structure → QB Time API format)
- Sync reliability and error handling (what happens when QB API is down or employee doesn't exist in QB?)

**Platform constraints:**
- CAF team owns QB integration infrastructure
- Payroll Squad owns HCP timesheet data and clock-in/out
- Cross-squad coordination required
- Must not break existing QB sync for invoices/payments/customers

**Data model considerations:**
- Need to determine: total hours only vs. hours per job vs. hours with cost codes
- Break time handling (already tracked in HCP, does QB need it?)
- Multi-day jobs across payroll periods
- Timesheet corrections and edits (how do updates sync?)

---

## Options

### Solution #1: Manual CSV Export (Quick Win)

Add a "Export to QuickBooks" button on the HCP timesheets page that generates a CSV file formatted for QuickBooks import. Office managers download the CSV and manually import it into QuickBooks Online using QB's native import feature.

| **Estimated Effort** | **T-Shirt Size or Sprints** |
| --- | --- |
| S - Simple export feature with minimal backend work. Assumes timesheet data is already accessible and CSV format requirements are straightforward. | 10 points |

| **In Scope** | **Out of Scope** |
| --- | --- |
| • Export button on timesheets page<br>• CSV generation with QB-compatible format<br>• Basic field mapping (employee name, date, hours)<br>• Date range selector (e.g., "last week", "last 2 weeks")<br>• Simple documentation on how to import to QB | • Automated sync<br>• Employee name validation/matching<br>• QB API integration<br>• Error handling for QB import<br>• Job-level hour breakdown<br>• Break time details |

| **Pros** | **Cons** |
| --- | --- |
| • Fast to ship (2-3 days)<br>• Minimal engineering complexity<br>• No QB API dependencies<br>• Immediate value for customers<br>• Low risk of breaking existing QB sync | • Still requires manual work (download + import)<br>• No validation that employee names match QB<br>• Error-prone (wrong date range, forgotten imports)<br>• Doesn't solve competitive gap vs. Jobber/ServiceTitan<br>• May not reduce churn significantly |

**Technical complexity:** Low. Backend generates CSV from existing timesheet data, frontend adds download button. No new infrastructure needed.

**Technical assumptions:**
- Timesheet data is already accessible via internal API
- QB's CSV import format is well-documented (need to verify exact field requirements)
- No complex data transformations required for basic hours export

**Dependencies:**
- Payroll Squad for timesheet data access
- Minimal - mostly self-contained feature

**Risks:**
- Customers may still be frustrated by manual step ("why can't it just sync automatically?")
- CSV format may not support all QB import scenarios (e.g., different formats for QB Desktop vs QB Online)
- If QB changes import format, CSV may break without us knowing

---

### Solution #2: Automated One-Way Sync to QBO Time Tracking (Recommended)

Build automated sync from HCP timesheets to QuickBooks Online's native Time Tracking feature (the same integration model Jobber uses). Timesheets automatically sync once per day, appearing in QB's "Time Activities by Employee Detail" report. Office managers enable sync with one click and employee hours flow automatically.

| **Estimated Effort** | **T-Shirt Size or Sprints** |
| --- | --- |
| M - Moderate complexity integration. Assumes QB Time API is well-documented, employee records already sync between HCP and QB, and no major data model changes needed. Could increase to L (40pts) if employee matching is complex or QB API has significant rate limiting/reliability issues. | 20 points |

| **In Scope** | **Out of Scope** |
| --- | --- |
| • One-way sync (HCP → QB) for total hours per employee per day<br>• Integration with QB Online Time Tracking API<br>• Employee name matching logic (HCP employee → QB employee)<br>• Daily batch sync (runs overnight)<br>• Settings page: enable/disable sync, last sync status<br>• Error notifications (e.g., "Sync failed: Employee 'John Doe' not found in QuickBooks")<br>• Basic retry logic for failed syncs | • Two-way sync (QB → HCP)<br>• Real-time sync (only daily batch)<br>• QB Desktop support<br>• QuickBooks Time (TSheets) app integration<br>• QB Payroll direct integration<br>• Job-level hour breakdown (v1 is total hours per day)<br>• Cost codes or service items<br>• Break time detail sync |

| **Pros** | **Cons** |
| --- | --- |
| • Fully automated - no manual steps for office managers<br>• Competitive parity with Jobber/ServiceTitan<br>• Addresses primary churn driver<br>• Scalable foundation for future enhancements<br>• Works with existing QB Online integration<br>• Reduces 30-60 min/week manual work per customer | • Limited to QB Online (doesn't solve QB Desktop users)<br>• Daily sync only (not real-time)<br>• Employee names must match exactly between systems<br>• v1 only syncs total hours, not job-level detail<br>• Doesn't integrate with QB Time (TSheets) app yet<br>• Adds ongoing maintenance burden (QB API changes) |

**Technical complexity:** Moderate. Requires new background job service, QB Time API integration, employee matching logic, and error handling. Builds on existing QB integration infrastructure but adds new sync entity (timesheets).

**Technical assumptions:**
- QB Time API supports creating time entries programmatically (need to verify API capabilities)
- Employee records are already synced or can be matched by name
- QB API rate limits allow daily batch sync for our customer volume
- Sync failures can be surfaced to users without requiring immediate support intervention
- One sync per day is acceptable (vs. real-time) for v1

**Dependencies:**
- **CAF Team (QB Integration Squad):** Core dependency - owns QB sync infrastructure, needs to build QB Time API integration
- **Payroll Squad:** Access to timesheet data model and clock-in/out records
- **QB Time API documentation and access:** Must verify API exists and supports our use case
- **Employee sync infrastructure:** May need to ensure employees sync to QB before timesheets can sync

**Risks:**
- **Employee matching failure:** If employee names don't match exactly between HCP and QB, sync will fail. Need clear error messages and guidance for customers.
- **QB API reliability:** If QB API has frequent downtime, syncs fail and customers lose trust in feature.
- **Scope creep:** Customers may immediately request job-level detail, real-time sync, QB Desktop support - need to hold boundary on v1 scope.
- **Support burden:** Failed syncs generate support tickets; need self-service troubleshooting.
- **Data model complexity:** If HCP timesheet structure is more complex than expected (e.g., split shifts, multi-day jobs), mapping to QB format may be harder.

---

### Solution #3: Comprehensive Multi-Product QB Integration

Comprehensive timesheet sync supporting QuickBooks Online, QuickBooks Desktop, QuickBooks Time (TSheets app), and QuickBooks Payroll. Includes job-level hour breakdown, cost codes, break time detail, real-time sync, two-way sync capabilities, and advanced configuration options.

| **Estimated Effort** | **T-Shirt Size or Sprints** |
| --- | --- |
| XL - Very large initiative requiring multiple teams, staged rollout, and significant complexity. Assumes we can register with all QB products and APIs are well-documented. Could increase to XXL (100pts) if QB Desktop API is legacy/difficult or QB Payroll integration requires compliance work. **Recommend breaking into phases rather than building all at once.** | 80 points |

| **In Scope** | **Out of Scope** |
| --- | --- |
| • Everything in Solution #2, plus:<br>• QB Desktop integration (different API/protocol)<br>• QuickBooks Time (TSheets) integration<br>• QB Payroll direct integration<br>• Job-level hour breakdown (hours per job, not just per day)<br>• Cost codes and service items<br>• Break time detail sync<br>• Real-time sync option (in addition to batch)<br>• Two-way sync (allow QB edits to flow back to HCP)<br>• Advanced settings: custom field mapping, sync frequency<br>• Multi-product support per org (e.g., one org uses QB Online + QB Time) | • Provincial tax registration (separate initiative)<br>• Payroll processing in HCP (that's HCP Payroll product)<br>• Custom QB workflows beyond standard time tracking |

| **Pros** | **Cons** |
| --- | --- |
| • Solves all QB timesheet use cases at once<br>• Future-proof architecture<br>• Supports all customer segments (QB Online, Desktop, Time, Payroll)<br>• Competitive differentiation (goes beyond Jobber/ServiceTitan)<br>• Flexible for complex workflows | • **Too large for immediate need** ($17K/month churn continues during 3-4 week build)<br>• **High risk of scope creep and delays**<br>• Requires multiple team coordination (CAF, Payroll, potentially Finance)<br>• Complex testing and QA across all QB products<br>• Significant ongoing maintenance burden (4+ QB APIs to maintain)<br>• May over-engineer for actual customer needs (do most customers need ALL of this?) |

**Technical complexity:** Very high. Multiple API integrations (QB Online, QB Desktop QBXML, QB Time, QB Payroll), complex data model mapping, two-way sync conflict resolution, real-time sync infrastructure, advanced configuration UI. Significant architectural planning needed.

**Technical assumptions:**
- All QB APIs are accessible and well-documented (QB Desktop uses legacy QBXML format which is notoriously difficult)
- We can build a generalized sync framework that handles multiple QB products
- Two-way sync conflict resolution is solvable (what happens if office manager edits timesheet in both HCP and QB?)
- Real-time sync infrastructure exists or can be built
- Team has capacity for 3-4 week initiative without other work slipping

**Dependencies:**
- CAF Team (QB Integration Squad) - extensive work across multiple QB products
- Payroll Squad - timesheet data model may need enhancements for job-level detail
- QB Time, QB Desktop, QB Payroll API access and documentation
- Potential Finance team involvement for QB Payroll integration
- Legal review for any payroll data handling compliance

**Risks:**
- **Waterfall trap:** Too large to ship iteratively, risk of "big bang" release that misses customer needs
- **Maintenance nightmare:** 4+ QB APIs to maintain, each with their own quirks and breaking changes
- **Analysis paralysis:** So many options and configurations that customers don't know what to choose
- **Delayed value:** Takes 3-4 weeks to ship while churn continues
- **Wrong priorities:** May be solving problems customers don't actually have (do they really need two-way sync?)
- **Team burnout:** Large, complex project across multiple squads could create coordination fatigue

---

## Decision and Outcome

| **Decision Selected** | **Changes** |
| --- | --- |
| Solution #[TBD] | [TBD] |

### Reasoning

[TBD]

| **Updated Estimated Effort** | **T-Shirt Size or Sprints** |
| --- | --- |
| | |

---

## Recommendation *(outside the doc — for PM use before the meeting)*

**Recommended path:** Solution #2 (Automated One-Way Sync to QBO Time Tracking)

**Why:** This is the "Goldilocks" option—automated enough to solve the churn problem and match competitor features, but scoped narrowly enough to ship in 1 week. Solution #1 (CSV export) doesn't fully solve the competitive gap and may not reduce churn significantly. Solution #3 is over-engineered for the actual customer need and delays value by 3-4 weeks. Solution #2 trades job-level detail and multi-product support for speed, but we can add those in v2 if customers actually need them (which is TBD). Most importantly, this gets us to competitive parity with Jobber (who also just syncs to QB Time Tracking) fast.

**Suggested next step:** Technical spike with CAF team (2-3 days) to validate:
1. Does QB Online Time API support programmatic time entry creation?
2. What are the exact field requirements and format?
3. What's the rate limiting and reliability story?
4. How do we handle employee matching (do employees already sync, or do we need to build that first)?
5. Does the M (20pt) estimate hold up, or should it be L (40pt)?

After technical spike, if assumptions hold, proceed with Solution #2. If QB API is more complex than expected or employee matching is a blocker, consider pivoting to Solution #1 as a fast interim solution while we figure out Solution #2.

---

## Open Questions for Engineering

**For CAF Team (QB Integration):**
- Does QB Online provide a Time Tracking API for programmatic time entry creation? What's the exact endpoint and authentication flow?
- What are the rate limits on QB Time API? Can it handle daily batch sync for ~14K orgs?
- How reliable is QB API? What's their uptime SLA and how should we handle failures?
- Do employees need to exist in QB before timesheets can sync, or can we create them on-the-fly?
- What's the employee matching strategy? Exact name match? QB employee ID? Email?

**For Payroll Squad:**
- What's the current timesheet data model? Is it easy to export daily hours per employee?
- Are there edge cases we need to handle (split shifts, multi-day jobs, timesheet corrections)?
- If we need job-level detail in v2, is that data structure already available or would it require changes?
- What's the API access pattern? Can we query timesheets for a date range efficiently?

**General Technical:**
- Does the M (20pt) estimate account for error handling, retry logic, and monitoring infrastructure?
- What would make this estimate change significantly? (e.g., QB API is more complex than expected, employee matching requires ML, etc.)
- Are there technical constraints I'm missing around sync frequency (why not real-time in v1)?
- Should this be built as part of existing QB sync service or as a separate microservice?
- What's the testing strategy? Do we need a QB sandbox environment?

**Product/Strategic:**
- Is daily batch sync acceptable for v1, or do customers need real-time?
- Is total hours per day sufficient, or do we need job-level breakdown immediately?
- Should we support QB Desktop in v1, or is QB Online enough to start?
- How do we message this to existing customers who've been asking for this feature?
- What's the rollout strategy? Phased by customer segment, or all-at-once?
