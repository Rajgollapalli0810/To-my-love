# Private Visitor Counter Setup

This site is hosted on GitHub Pages, so it needs a tiny online storage endpoint to remember visits. Use Google Apps Script with a Google Sheet.

## 1. Create the Google Sheet

1. Go to Google Sheets.
2. Create a new sheet named `Love Site Visits`.
3. Copy the spreadsheet ID from the URL.

Example URL:
`https://docs.google.com/spreadsheets/d/SPREADSHEET_ID_HERE/edit`

## 2. Create Apps Script

1. In the sheet, open `Extensions` > `Apps Script`.
2. Delete the default code.
3. Paste this code.
4. Change `SPREADSHEET_ID_HERE`.
5. Change `CHANGE_THIS_PRIVATE_PIN` to your private PIN.

```js
const SPREADSHEET_ID = "SPREADSHEET_ID_HERE";
const ADMIN_KEY = "CHANGE_THIS_PRIVATE_PIN";
const SHEET_NAME = "Visits";

function doGet(e) {
  const params = e.parameter || {};
  const callback = String(params.callback || "callback").replace(/[^\w$.]/g, "");
  const payload = handleRequest(params);
  return ContentService
    .createTextOutput(`${callback}(${JSON.stringify(payload)})`)
    .setMimeType(ContentService.MimeType.JAVASCRIPT);
}

function handleRequest(params) {
  const sheet = getSheet();
  if (params.action === "visit") {
    sheet.appendRow([
      new Date(),
      Utilities.formatDate(new Date(), Session.getScriptTimeZone(), "yyyy-MM-dd"),
      params.visitor || "",
      params.page || "",
      params.tz || "",
      params.version || "",
      params.userAgent || ""
    ]);
    return { ok: true };
  }

  if (params.action === "stats") {
    if (params.key !== ADMIN_KEY) return { ok: false, error: "wrong-key" };
    const values = sheet.getDataRange().getValues();
    const rows = values.slice(1);
    const today = Utilities.formatDate(new Date(), Session.getScriptTimeZone(), "yyyy-MM-dd");
    const todayCount = rows.filter((row) => row[1] === today).length;
    const lastSeen = rows.length ? rows[rows.length - 1][0] : "";
    return {
      ok: true,
      total: rows.length,
      today: todayCount,
      lastSeen
    };
  }

  return { ok: false, error: "unknown-action" };
}

function getSheet() {
  const ss = SpreadsheetApp.openById(SPREADSHEET_ID);
  let sheet = ss.getSheetByName(SHEET_NAME);
  if (!sheet) {
    sheet = ss.insertSheet(SHEET_NAME);
    sheet.appendRow(["Timestamp", "Date", "Visitor", "Page", "Timezone", "Version", "User Agent"]);
  }
  return sheet;
}
```

## 3. Deploy Apps Script

1. Click `Deploy` > `New deployment`.
2. Select type: `Web app`.
3. Execute as: `Me`.
4. Who has access: `Anyone`.
5. Click `Deploy`.
6. Copy the Web App URL.

## 4. Add URL To Website

Open `data.js` and paste the Web App URL here:

```js
visitorCounter: {
  enabled: true,
  endpoint: "PASTE_WEB_APP_URL_HERE"
},
```

Then commit and push the site.

## 5. View Your Private Counter

Normal link for her:
`https://rajgollapalli0810.github.io/To-my-love/`

Private counter link for you:
`https://rajgollapalli0810.github.io/To-my-love/?admin=YOUR_PRIVATE_PIN`

Keep the private PIN secret. Without that PIN, the stats request will not show the count.
