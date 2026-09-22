META Tag Extractor
What Is It?

META Tag Extractor turns a large list of URLs into a structured SEO audit report—extracting metadata, headings, canonicals, HTTP status, and potential issues at scale.

Instead of manually opening each page and checking its source code, the skill processes 10, 100, 1,000+ URLs and returns the key SEO elements in a structured CSV report.

It extracts:
META Title
Title Length
META Description
Description Length
H1 Tag
H2 Tag — first H2 only
Canonical Tag
HTTP Status Code
SEO Notes / Issues

If an element is missing, the result is reported as N/A.

Why Use It?
Manual SEO metadata checking is time-consuming, especially when auditing large websites.
For example, checking 500 URLs manually means repeatedly:
The META Tag Extractor automates this process and puts the results into one organized report.
Bulk URLs → automated extraction → structured SEO report
This makes it easier to identify SEO issues, prioritize fixes, and share findings with clients or development teams.

How Does It Work?
The workflow is simple:
Step 1 — Provide URLs
You can provide URLs in multiple ways:

Paste URLs directly
https://example.com/page-1
https://example.com/page-2
https://example.com/page-3

Upload a CSV
URL
https://example.com/page-1
https://example.com/page-2

Upload an XLSX file

The skill reads the URL column and processes the pages.

Google Sheet
Provide a shareable Google Sheet link containing the URLs.

Step 2 — Fetch Each URL
The skill accesses each URL and checks:

HTTP response status
Page HTML
<title>
Meta description
Headings <h1>
First <h2>
Canonical URL
It also identifies relevant issues such as missing elements, redirects, or extraction errors.

Step 3 — Extract SEO Elements
The extracted information is organized into structured fields.

Field	Purpose
URL	Page being audited
Status	HTTP response status
META Title	Current page title
Title Length	Character count
META Description	Current meta description
Description Length	Character count
H1 Tag	Primary page heading
H2 Tag	First H2 heading
Canonical	Declared canonical URL
Notes	Detected SEO issues
Step 4 — Analyze the Results
The skill checks for common issues

The skill provides:
Chat Summary with
A quick overview containing:
Total URLs processed
Successfully processed URLs
URLs with errors
Missing titles
Missing descriptions
Missing H1s
Missing H2s
Missing canonicals
Redirects
Other detected issues

And CSV Report
A complete downloadable report containing every processed URL and its extracted SEO data.

Benefit
Instead of manually auditing individual pages, SEO teams can identify issues across hundreds or thousands of URLs in a single workflow.
Helps SEO teams understand competitor page optimization and identify opportunities for better metadata and content structure.
It also creates a structured report that can be shared with clients or development teams.
This gives the SEO professional an immediate understanding of the website's condition.


