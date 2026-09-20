# Technical architecture

## Deliverable

`workbooks/customer_booking.xlsx` is a self-contained Excel workbook. It contains the data model, calculated fields, pivot reports, slicers, dashboard objects, and cached results. There are no VBA macros or external workbook links.

## Workbook architecture

| Sheet | Role |
| --- | --- |
| `customer_booking` | Primary booking dataset. Excel table `Table1` occupies `A1:O50001` and holds 50,000 booking records plus a calculated service indicator. |
| `Sheet1` | Pivot-based analysis supporting the question-style summaries such as booking status, completion by channel, flight-hour counts, duration, and extra-service usage. |
| `Sheet3` | Pivot matrix of booking completions by `flight_day` and `flight_hour`. |
| `Dashboard Source` | Intermediate dashboard metrics and linked values, including passenger totals and average flight, passenger, and stay metrics. |
| `Dashboard` | Presentation layer containing the visual dashboard objects. |

The logical flow is:

```text
Table1 booking data → pivot caches and pivot reports → dashboard source metrics → dashboard visuals
```

The workbook contains 17 pivot tables and slicer controls for `flight_day`, `flight_hour`, and `sales_channel`. Pivot caches and slicer definitions are native Excel features stored inside the `.xlsx` package.

## Data model

`Table1` contains these fields:

```text
num_passengers, sales_channel, trip_type, purchase_lead, length_of_stay,
flight_hour, flight_day, route, booking_origin, wants_extra_baggage,
wants_preferred_seat, wants_in_flight_meals, flight_duration,
booking_complete, Need Extra Service
```

`Need Extra Service` is a table formula. For each row, it returns `Yes` when any of baggage, preferred seat, or in-flight meals is `Yes`; otherwise it returns `No`. The formula uses structured `Table1` references, so adding rows within the table should continue the formula pattern automatically in Excel.

## Key decisions

- The repository is intentionally small because the workbook is the only functional artifact. Documentation lives at the project root and the deliverable lives in `workbooks/`.
- The workbook is moved without being rewritten or re-exported. This preserves pivot caches, slicers, chart objects, formatting, cached values, and Excel-specific metadata.
- Sheet and table names are treated as integration points. Renaming them can break pivot sources, structured references, slicer connections, or dashboard links.
- No environment variables, secrets, package manager files, or runtime services are required.

## Maintenance constraints

Use Excel Desktop for workbook edits that must retain pivot tables and slicers. Some general-purpose spreadsheet libraries do not fully preserve those native Excel features when saving a workbook.

When changing the source data, keep rows inside `Table1`, retain the existing headers and data types, refresh the workbook, and test the dashboard filters. If a field must be renamed or removed, update every dependent pivot, slicer, formula, and dashboard object before delivery.
