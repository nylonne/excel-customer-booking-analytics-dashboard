# Excel Customer Booking Analytics Dashboard

Interactive Excel dashboard for analyzing 50,000 customer booking records, conversion trends, services, and flight patterns. The workbook combines pivot-based analysis, slicers, and dashboard views for booking completion, routes, passenger counts, flight timing, and channel data.

## Project layout

```text
.
├── README.md
├── TECHNICAL.md
├── SETUP.md
└── workbooks/
    └── customer_booking.xlsx
```

`workbooks/customer_booking.xlsx` is the project deliverable and source of truth. Keep the workbook and its internal sheet names together when sharing or archiving the project.

## Using the workbook

1. Open `workbooks/customer_booking.xlsx` in the Excel desktop application.
2. Use the Dashboard and its slicers to explore the available booking views.
3. When the underlying booking data changes, use **Data > Refresh All** before reviewing the dashboard.
4. Save the workbook normally. Excel keeps the calculated service indicator, pivot reports, and dashboard state in the same file.

For the workbook internals and maintenance rules, see [TECHNICAL.md](TECHNICAL.md). For prerequisites, refresh steps, and a safe editing workflow, see [SETUP.md](SETUP.md).

## Important handling notes

- The workbook has no macros and no external workbook links.
- Do not rename `customer_booking`, `Sheet1`, `Dashboard Source`, `Dashboard`, or `Sheet3` without updating the dependent Excel objects.
- Do not rename `Table1` or its existing columns without checking the pivots and the structured formula that derives `Need Extra Service`.
