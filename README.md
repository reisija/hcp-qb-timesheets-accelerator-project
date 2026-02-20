# HCP QuickBooks Timesheet Sync

Product design and prototypes for synchronizing Housecall Pro timesheets with QuickBooks Online.

## 📁 Project Structure

```
├── README.md                           # This file
├── INSIGHTS_BRIEF.md                   # Research and problem space analysis
├── QUICK_REFERENCE.md                  # At-a-glance summary with key quotes
├── research-findings.md                # Detailed analysis of customer feedback
├── solution-options.md                 # Three solution approaches with sizing
├── top-50-snippets.json               # Raw customer feedback data
├── hcp-final-payroll-onboarding.html  # Payroll onboarding prototype
└── hcp-final-time-tracking.html       # Time tracking with sync features
```

## 🎨 Prototypes

### Payroll Onboarding
**File:** `hcp-final-payroll-onboarding.html`

Features:
- Step-by-step onboarding flow
- QuickBooks sync configuration step
- Automatic vs manual sync options
- Frequency scheduling (daily/weekly/monthly)
- Modal-based configuration UI

### Time Tracking
**File:** `hcp-final-time-tracking.html`

Features:
- Employee card view with sync status
- Success/error state indicators
- 3-dot menu with "Push timesheet to QuickBooks"
- Bulk action for multiple employees
- Sync History tab with table view
- 3/6/12 month history options with pagination

## 🎯 Key Metrics

- **TAM:** 15K QuickBooks Online organizations
- **Current Users:** 3K using HCP payroll
- **Churn Impact:** 6.62% QBO churn rate, 5.6% payroll churn rate

## 📊 Solution Options

1. **Manual CSV Export** (S / 10 points)
2. **Automated One-Way Sync** (M / 20 points) - RECOMMENDED
3. **Comprehensive Multi-Product Integration** (XL / 80 points)

See `solution-options.md` for detailed analysis.

## 🎨 Design System

All prototypes use the exact Housecall Pro design system:
- **Colors:** #0e6fbe (primary), #00a344 (success), #e91e63 (error)
- **Typography:** 14px body, 12px labels, 24px headings
- **Geometry:** 8px border-radius, 1px borders
- **Components:** Fully rounded buttons (200px)

## 📝 Version History

- **v1.0** - Initial prototypes with QB sync integration
- Design system compliant
- Interactive functionality with JavaScript

## 🚀 Viewing Prototypes

Simply open the HTML files in a web browser:
```bash
open hcp-final-payroll-onboarding.html
open hcp-final-time-tracking.html
```

## 🔧 Git Setup

This repository is configured with version control:
```bash
# View commit history
git log --oneline

# Create a new branch for changes
git checkout -b feature/new-feature

# Stage and commit changes
git add .
git commit -m "Description of changes"

# Push to GitHub (after creating remote repository)
git remote add origin https://github.com/reisija/hcp-qb-timesheets.git
git push -u origin main
```

## 📚 Research Sources

- 659 customer feedback snippets analyzed via Reforge MCP
- Confluence documentation published
- Competitive analysis included

---

**Last Updated:** February 20, 2026
**Status:** Ready for review
