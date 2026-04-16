# Blind Clinical Evaluation Platform

Expert rating platform for the prompt compression study. Adapted from the or-expert-eval project.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Expert rating interface (Hebrew RTL) |
| `admin.html` | Admin dashboard (manage experts, view data, download CSV) |
| `config.json` | Stimulus configuration (conversation pairs, dimensions, anchors) |

## Architecture

- **Frontend**: Static HTML/CSS/JS (no build, no npm)
- **Backend**: Google Apps Script (free, handles CORS, stores in Google Sheets)
- **Data flow**: `index.html` -> POST to Apps Script -> Google Sheets -> `admin.html` reads via GET

## Setup Instructions

### Step 1: Create Google Sheet

1. Go to [Google Sheets](https://sheets.google.com) and create a new spreadsheet
2. Name it: `Compression Eval Data`
3. Create two sheets (tabs):
   - `Experts` - columns: `id`, `name`, `role`, `years`, `created`
   - `Responses` - columns: all the data fields (auto-created on first submission)

### Step 2: Create Apps Script Backend

1. In the Google Sheet, go to **Extensions > Apps Script**
2. Delete any existing code and paste the following:

```javascript
var SPREADSHEET_ID = SpreadsheetApp.getActiveSpreadsheet().getId();

function doGet(e) {
  var action = (e && e.parameter && e.parameter.action) || 'responses';
  var ss = SpreadsheetApp.openById(SPREADSHEET_ID);

  if (action === 'experts') {
    return jsonResponse(getExperts(ss));
  }
  if (action === 'expert') {
    return jsonResponse(getExpert(ss, e.parameter.id));
  }
  if (action === 'my_responses') {
    return jsonResponse(getMyResponses(ss, e.parameter.expert_id));
  }
  // Default: return all responses
  return jsonResponse(getResponses(ss));
}

function doPost(e) {
  var data;
  try {
    data = JSON.parse(e.postData.contents);
  } catch(err) {
    return jsonResponse({error: 'Invalid JSON'});
  }

  var ss = SpreadsheetApp.openById(SPREADSHEET_ID);
  var action = data.action || 'submit_response';

  if (action === 'register_expert') {
    return jsonResponse(registerExpert(ss, data));
  }
  if (action === 'submit_response') {
    return jsonResponse(submitResponse(ss, data));
  }
  if (action === 'delete_expert') {
    return jsonResponse(deleteExpert(ss, data.id));
  }
  if (action === 'delete_response') {
    return jsonResponse(deleteResponse(ss, data.expert_id, data.pair_id));
  }
  if (action === 'clear_responses') {
    return jsonResponse(clearResponses(ss));
  }

  return jsonResponse({error: 'Unknown action'});
}

function jsonResponse(data) {
  return ContentService.createTextOutput(JSON.stringify(data))
    .setMimeType(ContentService.MimeType.JSON);
}

// --- EXPERTS ---

function getExperts(ss) {
  var sheet = ss.getSheetByName('Experts');
  if (!sheet) return {experts: []};
  var data = sheet.getDataRange().getValues();
  if (data.length <= 1) return {experts: []};
  var experts = [];
  for (var i = 1; i < data.length; i++) {
    experts.push({id: data[i][0], name: data[i][1], role: data[i][2] || '', years: data[i][3] || ''});
  }
  return {experts: experts};
}

function getExpert(ss, id) {
  var sheet = ss.getSheetByName('Experts');
  if (!sheet) return {error: 'Not found'};
  var data = sheet.getDataRange().getValues();
  for (var i = 1; i < data.length; i++) {
    if (String(data[i][0]) === String(id)) {
      return {id: data[i][0], name: data[i][1], role: data[i][2] || '', years: data[i][3] || ''};
    }
  }
  return {error: 'Not found'};
}

function registerExpert(ss, data) {
  var sheet = ss.getSheetByName('Experts');
  if (!sheet) {
    sheet = ss.insertSheet('Experts');
    sheet.appendRow(['id', 'name', 'role', 'years', 'created']);
  }
  var allData = sheet.getDataRange().getValues();
  var maxId = 0;
  for (var i = 1; i < allData.length; i++) {
    var id = parseInt(allData[i][0]);
    if (id > maxId) maxId = id;
  }
  var newId = maxId + 1;
  sheet.appendRow([newId, data.name, data.role || '', data.years || '', new Date().toISOString()]);
  return {id: newId, name: data.name};
}

function deleteExpert(ss, id) {
  var sheet = ss.getSheetByName('Experts');
  if (!sheet) return {ok: true};
  var data = sheet.getDataRange().getValues();
  for (var i = data.length - 1; i >= 1; i--) {
    if (String(data[i][0]) === String(id)) {
      sheet.deleteRow(i + 1);
    }
  }
  return {ok: true};
}

// --- RESPONSES ---

function getResponses(ss) {
  var sheet = ss.getSheetByName('Responses');
  if (!sheet) return {rows: []};
  var data = sheet.getDataRange().getValues();
  if (data.length <= 1) return {rows: []};
  var headers = data[0];
  var rows = [];
  for (var i = 1; i < data.length; i++) {
    var row = {};
    for (var j = 0; j < headers.length; j++) {
      row[headers[j]] = data[i][j];
    }
    rows.push(row);
  }
  return {rows: rows};
}

function getMyResponses(ss, expertId) {
  var sheet = ss.getSheetByName('Responses');
  if (!sheet) return {pairs: []};
  var data = sheet.getDataRange().getValues();
  if (data.length <= 1) return {pairs: []};
  var headers = data[0];
  var eidCol = headers.indexOf('expert_id');
  var pidCol = headers.indexOf('pair_id');
  var pairs = [];
  for (var i = 1; i < data.length; i++) {
    if (String(data[i][eidCol]) === String(expertId)) {
      var pid = data[i][pidCol];
      if (pairs.indexOf(pid) === -1) pairs.push(pid);
    }
  }
  return {pairs: pairs};
}

function submitResponse(ss, data) {
  var sheet = ss.getSheetByName('Responses');
  if (!sheet) {
    sheet = ss.insertSheet('Responses');
    // Create headers from data keys
    var keys = Object.keys(data).filter(function(k) { return k !== 'action'; });
    sheet.appendRow(keys);
  }
  var headers = sheet.getRange(1, 1, 1, sheet.getLastColumn()).getValues()[0];
  var row = [];
  for (var i = 0; i < headers.length; i++) {
    var val = data[headers[i]];
    row.push(val !== undefined ? val : '');
  }
  // Add any new columns
  var keys = Object.keys(data).filter(function(k) { return k !== 'action'; });
  keys.forEach(function(k) {
    if (headers.indexOf(k) === -1) {
      headers.push(k);
      sheet.getRange(1, headers.length).setValue(k);
      row.push(data[k] !== undefined ? data[k] : '');
    }
  });
  sheet.appendRow(row);
  return {ok: true};
}

function deleteResponse(ss, expertId, pairId) {
  var sheet = ss.getSheetByName('Responses');
  if (!sheet) return {ok: true};
  var data = sheet.getDataRange().getValues();
  var headers = data[0];
  var eidCol = headers.indexOf('expert_id');
  var pidCol = headers.indexOf('pair_id');
  for (var i = data.length - 1; i >= 1; i--) {
    if (String(data[i][eidCol]) === String(expertId) && String(data[i][pidCol]) === String(pairId)) {
      sheet.deleteRow(i + 1);
    }
  }
  return {ok: true};
}

function clearResponses(ss) {
  var sheet = ss.getSheetByName('Responses');
  if (!sheet) return {ok: true};
  if (sheet.getLastRow() > 1) {
    sheet.deleteRows(2, sheet.getLastRow() - 1);
  }
  return {ok: true};
}
```

3. Save the script (Ctrl+S)
4. Click **Deploy > New deployment**
5. Type: **Web app**
6. Execute as: **Me**
7. Who has access: **Anyone**
8. Click **Deploy**
9. Authorize when prompted
10. Copy the deployment URL (looks like `https://script.google.com/macros/s/.../exec`)

### Step 3: Configure the Platform

1. Open `index.html` in a browser (or serve via any web server)
2. Paste the Apps Script URL when prompted
3. The URL is saved in localStorage for future visits

### Step 4: Add Experts via Admin

1. Open `admin.html`
2. Paste the same Apps Script URL
3. Add experts by name
4. Copy their personalized links and send via email/WhatsApp
5. Expert links look like: `index.html?api=<SCRIPT_URL>&expert=<ID>`

## How It Works

### For Experts
1. Open their personalized link
2. See welcome screen with study description
3. Select a conversation pair to evaluate
4. Read both conversations (displayed as chat bubbles with tabs)
5. Rate each conversation on 7 dimensions (1-7 Likert)
6. Answer forced-choice question: "Which was generated with the full prompt?"
7. Rate confidence (1-5) and explain reasoning
8. Indicate training preference
9. Submit and move to next pair

### Blinding
- Conversations are labeled "A" and "B" (not by condition)
- Display order is randomized per session
- The mapping (A=33k or A=3k) is recorded in the data but hidden from the expert
- `forced_choice_correct` is auto-computed for analysis

### Data Columns
The CSV output includes:
- Expert demographics: `expert_id`, `expert_name`, `expert_role`, `expert_years`
- Pair info: `pair_id`, `pair_index`, `therapist_input_id`
- Condition mapping: `display_a_condition`, `display_b_condition`
- Per-conversation ratings: `a_dim_clinical_authenticity` through `b_dim_body_language_quality` (7 x 2 = 14 columns)
- Forced choice: `forced_choice_display`, `forced_choice_correct`, `confidence`, `forced_reasoning`
- Preference: `preference_display`, `preference_condition`, `overall_comments`

## Updating Stimuli

Edit `config.json` to add/change conversation pairs. The format is:

```json
{
  "pairs": [
    {
      "id": "pair_01",
      "therapist_input_id": "S1",
      "conversation_a": { "condition": "33k", "turns": [...] },
      "conversation_b": { "condition": "3k", "turns": [...] }
    }
  ]
}
```

Each turn: `{ "role": "therapist"|"client", "text": "Hebrew text with **\"verbal\"** and [body language]" }`

No code changes needed -- just update the JSON.
