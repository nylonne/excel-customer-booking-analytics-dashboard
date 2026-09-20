# Setup and development

## Requirements

- Microsoft Excel desktop, preferably Microsoft 365 or Excel 2019 or later.
- A local copy of this project folder.

No package installation, macro enablement, external data connection, environment variable, or credentials are required.

## Open the project

1. Keep the repository contents together.
2. Open `workbooks/customer_booking.xlsx` in Excel Desktop.
3. If Excel asks to update data, review the prompt and use **Data > Refresh All** to refresh the workbook's pivot-based reporting.
4. Open the `Dashboard` sheet and verify that the `flight_day`, `flight_hour`, and `sales_channel` slicers respond.

## Updating booking data

1. Work in a copy of the workbook or use version control before making structural changes.
2. Add or update records inside the `Table1` range on the `customer_booking` sheet. Keep the existing column names and data types.
3. Confirm that the `Need Extra Service` calculated column has filled through all relevant rows.
4. Select **Data > Refresh All** to refresh pivot tables and the dashboard.
5. Review `Sheet1`, `Sheet3`, `Dashboard Source`, and `Dashboard` for expected totals and filter behavior.
6. Save, close, and reopen the workbook to confirm the dashboard still renders correctly.

## Development rules

- Preserve the worksheet names, `Table1`, its columns, pivot tables, slicers, and dashboard objects unless their dependencies are updated in the same change.
- Make data changes within the Excel table. Do not paste values outside the table and assume they will feed pivot reports.
- Use Excel Desktop for save operations. Avoid tools that rewrite `.xlsx` files without full support for pivots, slicers, drawings, and cached report definitions.
- Do not add credentials or data exports to the repository. If future scripts generate exports, keep generated files outside `workbooks/` unless they are approved deliverables.

## Validation checklist

Before sharing a changed workbook:

- Refresh all pivot-based content.
- Test each slicer independently and together.
- Confirm booking totals and dashboard summary metrics are populated.
- Confirm the calculated `Need Extra Service` column contains the intended values for a sample of updated records.
- Save, close, and reopen the workbook without repair prompts.
