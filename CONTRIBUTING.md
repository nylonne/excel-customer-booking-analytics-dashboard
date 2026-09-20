# Contributing

## Branches

Create focused branches from `main`. Use names that identify the area of change, such as `docs/refresh-guide`, `data/booking-update`, or `dashboard/filter-fix`.

## Commit messages

Use concise, scoped commit messages:

```text
docs: clarify workbook refresh workflow
data: update booking records for September
feat: add route analysis pivot
fix: correct service indicator formula
chore: update repository configuration
```

Keep data updates, dashboard changes, and documentation changes separate when practical. This makes workbook history easier to review and revert.

## Workbook changes

Before opening a pull request:

1. Make changes in Excel Desktop.
2. Refresh all pivot-based reporting.
3. Test the dashboard slicers for `flight_day`, `flight_hour`, and `sales_channel`.
4. Confirm the `Need Extra Service` formula fills correctly for changed or added records.
5. Save, close, and reopen the workbook without repair prompts.

Avoid renaming sheets, `Table1`, or existing data columns unless every dependent pivot, slicer, formula, and dashboard object is updated in the same pull request.
