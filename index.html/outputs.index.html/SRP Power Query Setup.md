# SRP Power Query Setup

## Data Source

Use the Power BI connector path:

1. Home
2. Get Data
3. More
4. Online Services
5. SharePoint Online List
6. Paste the SharePoint site URL, not the list URL
7. Select `SRP Patient Flow Tracker`
8. Select `Transform Data`

## Keep These Columns

- Tracking ID
- Rank/Last Name
- Unit
- Visit Type
- Arrival Time
- Current Step
- Assigned Staff
- Provider Needed
- Provider Start Time
- Provider End Time
- Disposition
- Primary Care Referral
- Delay Reason
- Completed Time

## Recommended Type Settings

| Column | Type |
| --- | --- |
| Tracking ID | Text |
| Rank/Last Name | Text |
| Unit | Text |
| Visit Type | Text |
| Arrival Time | Date/Time |
| Current Step | Text |
| Assigned Staff | Text |
| Provider Needed | True/False |
| Provider Start Time | Date/Time |
| Provider End Time | Date/Time |
| Disposition | Text |
| Primary Care Referral | True/False |
| Delay Reason | Text |
| Completed Time | Date/Time |

## Optional Power Query M Cleanup

Paste this into Advanced Editor after connecting, then replace the `Source` step with your connector source if needed.

```powerquery
let
    Source = #"SRP Patient Flow Tracker",
    KeepColumns = Table.SelectColumns(
        Source,
        {
            "Tracking ID",
            "Rank/Last Name",
            "Unit",
            "Visit Type",
            "Arrival Time",
            "Current Step",
            "Assigned Staff",
            "Provider Needed",
            "Provider Start Time",
            "Provider End Time",
            "Disposition",
            "Primary Care Referral",
            "Delay Reason",
            "Completed Time"
        }
    ),
    ChangedTypes = Table.TransformColumnTypes(
        KeepColumns,
        {
            {"Tracking ID", type text},
            {"Rank/Last Name", type text},
            {"Unit", type text},
            {"Visit Type", type text},
            {"Arrival Time", type datetime},
            {"Current Step", type text},
            {"Assigned Staff", type text},
            {"Provider Needed", type logical},
            {"Provider Start Time", type datetime},
            {"Provider End Time", type datetime},
            {"Disposition", type text},
            {"Primary Care Referral", type logical},
            {"Delay Reason", type text},
            {"Completed Time", type datetime}
        }
    )
in
    ChangedTypes
```
