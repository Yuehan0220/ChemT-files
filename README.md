# Gmail → Google Sheets CRM Automation (Apps Script)

This project is a Google Apps Script that turns Gmail + Google Sheets into a lightweight CRM for tracking **prospective and current customers** automatically.

It runs entirely in the background using time-based triggers—no manual updates required after setup.

---

## ✨ Key Features

- **Two parallel pipelines**
  - Prospective Customers
  - Current Customers
- **Automatic email tracking**
  - First contact date
  - Last contact date
  - Total email count
  - Last email timestamp
  - Short conversation summary
- **Gmail label → customer list sync**
  - Label a thread as:
    - `prospective customer` → added to *Prospective Customer List*
    - `current customer` → added to *Current Customer List*
  - Automatically excludes internal team emails (e.g. `@chemtbio.com`)
- **Follow-up detection**
  - Flags threads needing follow-up after inactivity
  - Applies a Gmail label (e.g. `Needs Follow-up`)
  - Optionally stars the email
- **Fully automated**
  - Runs on time-driven triggers
  - Can also be run manually on demand

---

## 📄 Required Google Sheets Tabs

Create the following tabs (exact names):

**Customer Lists**
- `Prospective Customer List`
- `Current Customer List`  
(Emails in column A)

**Customer Trackers**
- `Prospective Customer Tracker`
- `Current Customer Tracker`  
(Headers are auto-created on first run)

---

## 🏷 Required Gmail Labels

Create these Gmail labels (case-sensitive):
- `prospective customer`
- `current customer`
- `Needs Follow-up` (or change in config)

---

## ⚙️ Configuration

Edit the `CONFIG` object to control behavior:

- Lookback window (`hoursToCheck`)
- Follow-up timing (`daysUntilFollowup`)
- Gmail labels
- Internal domains to exclude
- Scan limits per run

Example:
```js
excludeDomains: ['chemtbio.com']
