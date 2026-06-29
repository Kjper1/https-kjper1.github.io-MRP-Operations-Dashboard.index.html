# SRP Operations Center Dashboard

This build pack gives you the pieces to create the Power BI report from the SRP Patient Flow Tracker list.

## Files

- `SRP Patient Flow Tracker Sample Data.csv`: fake test data for early dashboard building
- `SRP Power BI Measures.dax`: measures to paste into Power BI Desktop
- `SRP Power Query Setup.md`: cleanup steps and optional Power Query code
- `SRP Power BI Theme.json`: importable report theme

## Report Page

Create one page named `Operations Center`.

Top KPI row:

| Visual | Field |
| --- | --- |
| Card | Total Checked In |
| Card | Completed |
| Card | Waiting Provider |
| Card | Primary Care Referrals |
| Card | Same Day Completion Rate |

Middle row:

| Visual | Fields |
| --- | --- |
| Clustered bar chart | Axis: Current Step; Values: Total Checked In |
| Bar chart | Axis: Delay Reason; Values: Total Checked In |
| Bar chart | Axis: Assigned Staff; Values: Open Cases |

Bottom row:

Use a table named `Provider Queue`.

Fields:

- Tracking ID
- Rank/Last Name
- Unit
- Arrival Time
- Current Step
- Assigned Staff
- Delay Reason
- Provider Wait Minutes
- Provider Wait Status

Filter the table to show:

- Current Step is `Ready for Provider`
- Current Step is `Provider Evaluation`
- Current Step is `Additional Actions Needed`

## Conditional Formatting

Apply conditional formatting to `Provider Wait Status` or `Provider Wait Minutes`.

| Status | Color |
| --- | --- |
| Green | `#2E7D32` |
| Yellow | `#F9A825` |
| Red | `#C62828` |

## Suggested Slicers

- Unit
- Visit Type
- Current Step
- Assigned Staff

## Privacy Guardrail

Keep the public or monitor view limited to operational flow. Do not display full names, SSNs, diagnoses, clinical details, or sensitive notes on screens visible outside a controlled staff area.

## Publish

Publish the report to the approved workspace, then add the report as a Teams tab named `SRP Dashboard`.
