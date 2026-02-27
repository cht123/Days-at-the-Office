You are updating the RTO (Return-to-Office) Tracker for daysattheoffice.com.

## What this command does

Search the web for new company RTO policy announcements, update the existing data file with any new companies or policy changes, and commit/push the changes.

## Step-by-step instructions

### 1. Read the current data

Read the file `tools/rto-tracker/data.json`. This is a JSON array of company objects. Count the total companies and note the current state.

### 2. Search for new RTO announcements

Use WebSearch to find recent RTO policy announcements. Run at least 5 searches with queries like:

- "return to office mandate 2026"
- "company RTO policy announcement"
- "return to office requirement new"
- "hybrid work policy change 2026"
- "company requiring employees back to office"

Also search for updates to companies already in the tracker — policies may have changed (e.g., a company that was 3 days may have moved to 4 or 5).

### 3. For each new company or change found

Use WebFetch on the source article URL to verify the details before adding. Confirm:
- The company name
- The number of required days (5, 4, 3, "flex", or "remote")
- The effective date
- Key details

### 4. Update the JSON file

Edit `tools/rto-tracker/data.json`. Each entry MUST follow this exact schema:

```json
{
    "company": "Company Name",
    "industry": "Industry Category",
    "days": 5,
    "date": "YYYY-MM",
    "details": "One to two sentence summary of the policy.",
    "source": "https://full-url-to-source-article",
    "sourceLabel": "Publication Name"
}
```

**Field rules:**
- `company`: Full company name (e.g., "JPMorgan Chase", not "JPM")
- `industry`: One of: Tech, Finance, Telecom, Media, Pharma, Retail, Manufacturing, Automotive, Travel, Government, Advertising, Food & Beverage, Real Estate, Consulting, Defense, Healthcare, Energy, Insurance, Consumer Goods
- `days`: Use a number (5, 4, 3) for required days, or the string "flex" for flexible/hybrid-friendly, or "remote" for remote-first
- `date`: Format YYYY-MM for when the policy took/takes effect
- `details`: Brief, factual, 1-2 sentences. Include specific details like number of employees affected, enforcement mechanisms, or notable context
- `source`: Full URL to the news article or official announcement. Use "" if no source found
- `sourceLabel`: Short publication name (e.g., "Bloomberg", "CNBC", "Reuters", "The Verge"). Use "" if no source

**Important rules:**
- Do NOT add duplicate companies. If a company already exists, UPDATE the existing entry instead
- If a company's policy has changed (e.g., went from 3 days to 5 days), update the existing entry with the new policy and new source
- Keep entries sorted roughly by days (5-day first, then 4, 3, flex, remote) for readability
- The file must be valid JSON — no trailing commas, no comments
- Only add companies where you have reasonable confidence in the accuracy of the policy

### 5. Update the last-updated date

Edit `tools/rto-tracker/index.html` and update the "Last updated" date in the HTML to today's date. Find the line that looks like:

```html
<p class="last-updated">... Last updated: <strong>February 21, 2026</strong> ...
```

Update the date to today.

### 6. Update the FAQ answers if needed

If the set of companies requiring 5 days has changed significantly, update the FAQ answer in `tools/rto-tracker/index.html` that lists companies requiring 5-day attendance. Also update the corresponding FAQ Schema JSON-LD in the `<head>`.

### 7. Validate

Run this command to validate the JSON:
```
python3 -c "import json; data=json.load(open('tools/rto-tracker/data.json')); print(f'{len(data)} companies, valid JSON')"
```

### 8. Set up git credentials

Before committing, configure HTTPS push access by reading the token from `.env`:

```bash
cd tools/rto-tracker/../../  # repo root
export $(grep GITHUB_TOKEN .env)
git remote set-url origin https://github.com/BestDayLabs/Days_at_the_Office_Website.git
git config credential.helper store
echo "https://cht123:${GITHUB_TOKEN}@github.com" > ~/.git-credentials
git config user.email "michaelxtaylor@gmail.com"
git config user.name "Michael Taylor"
```

### 9. Commit and push

Stage the changed files, commit with a descriptive message like:

```
Update RTO tracker: X companies (added Y, updated Z)
```

Then push to origin/main.

### 10. Report

Tell the user:
- How many total companies are now in the tracker
- Which companies were added (list them)
- Which companies were updated (list changes)
- Any notable trends (e.g., "3 more companies moved to 5-day mandates this month")
