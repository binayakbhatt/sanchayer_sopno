# Sanchayer Sopno — GitHub Pages package

## Files
- `index.html`: responsive image-free campaign website, savings calculator, chart, full-horizon month-wise schedule, PDF report with FAQ, profession field, mandatory name/phone/PIN validation, FAQ accordion, and PLI/RPLI interest popup.
- `Code.gs`: Google Apps Script endpoint that stores customers, calculations, monthly schedule rows, and insurance-interest leads in Google Sheets.

## Publish on GitHub Pages
1. Create or open a public GitHub repository.
2. Upload `index.html` to the repository root and commit it.
3. Go to Settings → Pages. Select `Deploy from a branch`, branch `main`, folder `/(root)`, and Save.
4. Wait for GitHub Pages to publish the site.

## Configure Google Sheets
1. Create a Google Sheet.
2. Open Extensions → Apps Script and replace the editor code with `Code.gs` from this package.
3. Save the script.
4. Deploy → New deployment → Web app. Execute as: Me. Choose an access setting compatible with the site. If using a public static GitHub Pages website, the endpoint may need to be accessible to anyone.
5. Copy the deployed Web app URL ending in `/exec`.
6. In `index.html`, replace `PASTE_YOUR_APPS_SCRIPT_WEB_APP_URL_HERE` in `GOOGLE_SHEETS_WEB_APP_URL` with the actual URL.
7. Commit the updated `index.html` to GitHub and wait for redeployment.

## Important security note
At the user's request, staff access-code validation has been removed. Anyone who obtains the public Apps Script URL may submit data to it, so unwanted or fraudulent submissions are possible. Keep the spreadsheet private, monitor records, and consider an authenticated proxy or other stronger access controls before public launch. The browser uses `no-cors`, so it cannot verify the server response; test with dummy data and check the sheet directly.

## Calculation notes
- Interest rate is editable for scenario testing and defaults to 6.9% p.a.; it is not a live rate feed. Verify the currently notified Post Office TD rate before booking.
- Horizons support 1–10 years (up to 120 months). Plan A models contributions in the first 12 months only; Plan B contributes monthly throughout the selected horizon; Plan C steps up the monthly contribution annually throughout the selected horizon.
- The model uses a simplified quarterly-compounding approximation and assumes the entered rate remains unchanged for reinvestment. Actual future TD rates may change; actual maturity amounts, premature closure, taxes/TDS, rounding and product-specific rules are not calculated exactly.
- The PDF is the only report download and includes the projection graph, month-wise schedule and a concise FAQ section.
- The family-protection popup appears when the month-wise projection table is reached for monthly contributions of ₹2,000 or more. A “Yes” response is submitted to the `InsuranceInterests` tab.
