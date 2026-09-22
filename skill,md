---
name: meta-tag-extractor
description: Extract META title, description, H1, first H2, and canonical tags from URL lists. Accepts pasted URLs, CSV files, XLSX files, or Google Sheet links. No URL limit—process 10, 100, or 1000+ URLs at once. Outputs CSV file and chat table summary. Shows actual canonical URL (not match status). Perfect for SEO audits, competitor analysis, bulk site reviews, and content audits.
compatibility: URL fetch, file upload, CSV, XLSX, Google Sheets (optional)
---

# META Tag Extractor

Bulk extract key META tags and headings from any list of URLs instantly.

## What This Does

Extracts from every URL in your list:
- **META Title** - Page title tag content
- **Title Length** - Character count (ideal: 50-60)
- **META Description** - Meta description text
- **Description Length** - Character count (ideal: 150-160)
- **H1 Tag** - Main heading text
- **H2 Tag** - First subheading text only
- **Canonical Tag** - Actual canonical URL (not match status)
- **HTTP Status** - Status code (200, 404, 500, etc.)
- **Notes** - Issues, missing tags, redirects

Shows `N/A` if any tag is missing or page not accessible.

**No URL limit.** Process 10, 1000, or 10,000+ URLs at once.

## How to Use

### Step 1: Provide URL List

**Option A: Paste URLs (one per line)**
```
https://example.com/blog-1
https://example.com/blog-2
https://example.com/blog-3
```

**Option B: Upload CSV File**
```
url
https://example.com/page-1
https://example.com/page-2
https://example.com/page-3
```

**Option C: Upload XLSX File**
- Column A header: "url"
- Each URL in row below

**Option D: Google Sheet Link**
- Share link to your Google Sheet
- URLs in first column

### Step 2: Request Extraction
Say: "Extract META tags from these URLs" + [URLs/file/link]

### Step 3: Get Results
- **Chat table** — Sample rows + stats
- **CSV file** — All results, easy to import

---

## Step-by-Step Process

### 1. Parse Input
Accept:
- Pasted URL list (one per line, auto-detect)
- CSV import (auto-detect URL column)
- XLSX import (reads first column or finds "url" header)
- Google Sheet URL (reads via API)

Clean URLs:
- Remove whitespace
- Validate format
- Flag invalid URLs
- Preserve trailing slashes

### 2. Fetch Each Page
For each URL:
- Send HTTP request
- Record HTTP status (200, 301, 404, 500, etc.)
- If accessible: Parse HTML
- If 4xx/5xx: Record error, continue
- If timeout (>10 sec): Mark and continue

### 3. Extract META Tags

**META Title**:
- Read `<title>` tag content
- Record character count
- If missing: Show "N/A"

**META Description**:
- Read `<meta name="description">` content
- Record character count
- If missing: Show "N/A"

**H1 Tag**:
- Read first `<h1>` element
- Take text only (strip HTML)
- If missing: Show "N/A"

**H2 Tag**:
- Read FIRST `<h2>` element only
- Ignore all subsequent H2s
- Take text only (strip HTML)
- If missing: Show "N/A"

**Canonical Tag**:
- Read `<link rel="canonical" href="">` 
- Show ACTUAL URL value (not match/mismatch)
- If missing: Show "N/A"
- If different from page URL: Note in column

**HTTP Status**:
- Record exact status code (200, 301, 404, 500, etc.)
- 200 = Success
- 3xx = Redirect (will follow 1 redirect)
- 4xx/5xx = Error

### 4. Handle Errors

| Scenario | Output |
|----------|--------|
| Tag doesn't exist | N/A |
| Page 404/5xx | N/A for tags, status shown |
| Timeout (>10 sec) | "Timeout" in status |
| SSL error | Try without SSL, note if failed |
| Redirect (301/302) | Follow 1 redirect, extract from destination |
| Empty tag | N/A |

### 5. Generate Output

**Chat Table** (shows all URLs):
| URL | Status | Title (Len) | Description (Len) | H1 | H2 | Canonical | Notes |
|-----|--------|------------|-------------------|-----|-----|-----------|-------|
| [URL] | [Code] | [Title (XX)] | [Desc (XX)] | [H1] | [H2] | [Canonical URL] | [Issues] |

**CSV File** (all columns, ready to import):
- URL
- Status
- META Title
- Title Length
- META Description
- Desc Length
- H1 Tag
- H2 Tag
- Canonical Tag
- Notes

---

## Output Formats

### Chat Table Example

| URL | Status | META Title | Title Len | META Description | Desc Len | H1 Tag | H2 Tag | Canonical Tag | Notes |
|-----|--------|------------|-----------|------------------|----------|--------|--------|---------------|-------|
| https://example.com/page-1 | 200 | Complete Guide to Email Marketing | 34 | Learn email marketing best practices and strategies to grow your list and increase engagement. | 98 | The Complete Email Marketing Guide | Best Practices for List Growth | https://example.com/page-1 | ✓ Optimized |
| https://example.com/page-2 | 200 | Product Overview | 16 | N/A | N/A | Our Product Features | N/A | https://example.com/page-2 | Missing description & H2 |
| https://example.com/page-3 | 404 | N/A | N/A | N/A | N/A | N/A | N/A | N/A | Page not found |
| https://example.com/page-4 | 200 | Home | 4 | N/A | N/A | Welcome to Our Site | N/A | https://example.com/homepage | Different canonical URL |

### CSV File Structure

```csv
URL,Status,META Title,Title Length,META Description,Desc Length,H1 Tag,H2 Tag,Canonical Tag,Notes
https://example.com/page-1,200,Complete Guide to Email Marketing,34,Learn email marketing best practices...,98,The Complete Email Marketing Guide,Best Practices for List Growth,https://example.com/page-1,✓ Optimized
https://example.com/page-2,200,Product Overview,16,N/A,N/A,Our Product Features,N/A,https://example.com/page-2,Missing description & H2
https://example.com/page-3,404,N/A,N/A,N/A,N/A,N/A,N/A,N/A,Page not found
https://example.com/page-4,200,Home,4,N/A,N/A,Welcome to Our Site,N/A,https://example.com/homepage,Different canonical URL
```

---

## Chat Summary Shows

After extraction:
- **Total URLs processed**: X
- **Successful (200)**: X
- **Redirects (301/302)**: X
- **Errors (404/5xx)**: X
- **Timeouts**: X
- **Complete (all tags present)**: X
- **Incomplete (missing tags)**: X

Plus table of all results.

---

## Real-World Use Cases

### Use Case 1: SEO Audit Your Own Site

**Input**: List of 50 blog URLs from your site
```
https://yoursite.com/blog-post-1
https://yoursite.com/blog-post-2
[... 48 more]
```

**Output**: Identify pages with:
- Missing META descriptions
- Missing H1 tags
- Missing H2s
- Incorrect canonical tags

**Action**: Fix high-priority gaps

---

### Use Case 2: Competitor Analysis

**Input**: 20 competitor URLs
```
https://competitor.com/article-1
https://competitor.com/article-2
[... 18 more]
```

**Output**: See competitor META strategy:
- How long are their titles?
- What keywords in descriptions?
- H1/H2 structure
- Canonical strategy

**Action**: Adjust your own meta strategy to compete

---

### Use Case 3: Bulk Client Site Review

**Input**: 100+ client URLs
```
https://client1.com/page-1
https://client1.com/page-2
https://client2.com/page-1
[... 97 more]
```

**Output**: Spreadsheet showing all metadata + issues

**Action**: Send audit report with recommendations

---

### Use Case 4: Content Audit

**Input**: Your entire blog (1000+ URLs)
```
https://yourblog.com/post-1
https://yourblog.com/post-2
[... 998 more]
```

**Output**: Identify:
- Pages without descriptions
- Orphaned pages (no H1)
- Short/long titles
- Canonical issues

**Action**: Prioritize content updates

---

## Character Count Guidelines

| Element | Too Short | Ideal | Too Long |
|---------|-----------|-------|----------|
| Title | <30 | 50-60 | >70 |
| Description | <120 | 150-160 | >170 |
| H1 | <8 words | 8-10 words | >15 words |

---

## Tips for Best Results

1. **Clean URLs**: Remove tracking parameters if not needed
   - Keep: `https://example.com/page`
   - Remove: `https://example.com/page?utm_source=email`

2. **Use CSV for bulk**: Better than pasting 100+ URLs

3. **Review status codes**: 404s, 5xx, timeouts need investigation

4. **Read notes column**: Flags missing tags, redirects, issues

5. **Sort by status**: In CSV, filter to see only errors first

6. **Check character counts**: Identify titles/descriptions outside ideal range

7. **Track canonical issues**: Mismatch = potential duplicate issues

---

## What N/A Means

| Scenario | Shows |
|----------|-------|
| Tag doesn't exist on page | N/A |
| Page 404/5xx/timeout | N/A |
| Tag exists but empty | N/A |
| Canonical missing (default to URL) | N/A |
| H2 missing | N/A |

---

## Limits & Considerations

| Factor | Detail |
|--------|--------|
| URL Limit | None—process 1 to 10,000+ URLs |
| Processing Time | ~1-5 sec per URL (depends on page load) |
| Timeout | If URL takes >10 sec, marked "Timeout" |
| SSL/HTTPS | Handled automatically |
| Rate Limiting | Respects server limits, retries if needed |
| JavaScript Content | Cannot extract JS-rendered content (HTML only) |
| Redirects | Follows 1 redirect, extracts from destination |

---

## Multi-Client Workflow

1. Create separate input file per client
2. Extract tags for Client A (100 URLs)
3. Save as `Client-A-META-Audit.csv`
4. Extract for Client B (200 URLs)
5. Save as `Client-B-META-Audit.csv`
6. Share CSV with clients or import to your reports
7. Build recommendations from results

---

## Common Next Steps After Extraction

1. **Filter for errors**: Show only 404s, 5xx, timeouts
2. **Identify gaps**: Filter for "N/A" in description or H1
3. **Flag short titles**: < 30 characters
4. **Flag long titles**: > 70 characters
5. **Flag short descriptions**: < 120 characters
6. **Flag long descriptions**: > 170 characters
7. **Find canonical mismatches**: Different from page URL
8. **Review incomplete metadata**: Missing H2s or descriptions
9. **Compare to competitors**: See if structure is competitive
10. **Prioritize fixes**: Start with 200s that have N/A tags

---

## Exporting & Sharing

**CSV file is ready to**:
- Open in Excel/Google Sheets
- Import to SEO tools (Ahrefs, SEMrush, Moz)
- Share directly with clients
- Analyze in your own reports
- Filter and sort for presentations
- Track changes over time

---

## Example: Real Extraction

**Input URLs**:
```
https://kenscio.com/
https://kenscio.com/products/cert/
```

**Chat Output**:

| URL | Status | META Title | Title Len | Description | Desc Len | H1 | H2 | Canonical | Notes |
|-----|--------|------------|-----------|-------------|----------|-----|-----|-----------|-------|
| https://kenscio.com/ | 200 | Leading Email Marketing Company & Omnichannel Marketing Solutions in India – Kenscio | 102 | Kenscio is a leading omnichannel marketing platform and email marketing company in India offering messaging solutions across email SMS WhatsApp and automation to drive customer engagement and business growth. | 168 | Connect. Convert. Retain. | DISCOVER YOUR PERFECT FIT | https://kenscio.com/ | Title too long (102 chars) |
| https://kenscio.com/products/cert/ | 200 | KenCERT: Affordabel Omni-Channel Marketing Automation Solution in India – Kenscio | 98 | KenCERT is Kenscio's customer data platform and customer engagement tool that unifies customer information into a single view of customer data powers multi-channel marketing automation and enables personalized experiences through a 360 customer view. | 214 | KenCERT - Unparalleled Customer Engagement & Retention | Unified Customer View | https://kenscio.com/products/cert/ | Title too long (98 chars) - Typo: Affordabel |

**Stats**:
- Total URLs: 2
- Successful: 2
- Missing tags: 0
- Issues found: 2 (long titles, 1 typo)

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "Page not accessible" (404/5xx) | Check URL is correct, site is live |
| All tags show "N/A" | Page may be JS-rendered or not accessible |
| Taking too long | Large extraction? Process in smaller batches |
| Some URLs timeout | Add to "retry" list, try again later |
| Canonical looks wrong | Page might be redirecting—check manually |
| Title/description empty | Page might not have meta tags set |
| Getting duplicates | Remove duplicate URLs from input |

---

## Notes

- **JavaScript rendering**: Extracts from static HTML only. Heavy JS = some content may not appear
- **Rate limiting**: Large extractions may take longer to respect server limits
- **Redirects**: Follows 1 redirect, extracts from destination
- **International**: Works with any language/charset
- **Batch processing**: For 1000+ URLs, consider processing in batches of 500
- **Canonical defaults**: If missing, you may need to check manually

---

## How to Call This Skill

### Natural Language
- "Extract META tags from these URLs"
- "Get META title and description from this list"
- "Run META tag extraction on my competitor URLs"
- "Pull meta data from these 50 pages"

### Direct Command
```
Extract META tags from:
https://example.com/page-1
https://example.com/page-2
```

### From File
- "Extract META tags from this CSV"
- "Pull meta tags from my uploaded URLs"
- "Process this Google Sheet and extract tags"

---

## Output Filenames

- `[domain]-meta-extraction.csv` — CSV results
- Shared as table in chat with stats

**Keep organized**:
- `Client-A-META-Audit.csv`
- `Client-B-META-Audit.csv`
- `Competitor-Analysis-META.csv`
- `Site-Audit-[Date].csv`
