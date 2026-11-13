# Corpus

Public documents from SEC EDGAR for NVIDIA Corporation (CIK 0001045810). Downloaded 16 October 2026.

| File | Document | Period | Filed | Original on SEC EDGAR | Filing index (all exhibits) |
| --- | --- | --- | --- | --- | --- |
| `nvda-10k-fy2026.htm` | Form 10-K, fiscal year 2026 | FY ended 2026-01-25 | 2026-02-25 | https://www.sec.gov/Archives/edgar/data/1045810/000104581026000021/nvda-20260125.htm | https://www.sec.gov/Archives/edgar/data/1045810/000104581026000021/0001045810-26-000021-index.htm |
| `nvda-q4fy26-press-release.htm` | 8-K Exhibit 99.1, earnings press release | Q4 FY2026 | 2026-02-25 | https://www.sec.gov/Archives/edgar/data/1045810/000104581026000019/q4fy26pr.htm | https://www.sec.gov/Archives/edgar/data/1045810/000104581026000019/0001045810-26-000019-index.htm |
| `nvda-q4fy26-cfo-commentary.htm` | 8-K Exhibit 99.2, CFO commentary | Q4 FY2026 | 2026-02-25 | https://www.sec.gov/Archives/edgar/data/1045810/000104581026000019/q4fy26cfocommentary.htm | https://www.sec.gov/Archives/edgar/data/1045810/000104581026000019/0001045810-26-000019-index.htm |
| `nvda-10q-q2fy2027.htm` | Form 10-Q, second quarter fiscal 2027 | quarter ended 2026-07-26 | 2026-08-26 | https://www.sec.gov/Archives/edgar/data/1045810/000104581026000075/nvda-20260726.htm | https://www.sec.gov/Archives/edgar/data/1045810/000104581026000075/0001045810-26-000075-index.htm |
| `nvda-companyfacts.json` | XBRL company facts, trimmed to 10-K/10-Q facts from fiscal 2025 onwards | | | https://data.sec.gov/api/xbrl/companyfacts/CIK0001045810.json | |
| `eval/questions.json` | 15 evaluation questions with gold answers, written by hand from the documents above | | | | |

How to get them yourself:

- **In a browser.** Every NVIDIA filing is listed at https://www.sec.gov/edgar/browse/?CIK=1045810 (filter by form type: 10-K, 10-Q, 8-K). Open a filing index to see its documents; in the 8-K of 25 February 2026 the press release is Exhibit 99.1 and the CFO commentary Exhibit 99.2.
- **Live in the notebook.** Section 0 has a table of these links and a cell that downloads the press release from EDGAR and checks it against the copy here. A fresh download is not byte-identical to the file in this folder: EDGAR's web server appends a `<script>` tag with a random path to every response. Without that tag the documents are the same.

EDGAR access rules: send a `User-Agent` header naming your organisation and a contact email, and stay under ten requests per second. Cloud notebooks are sometimes rate-limited by EDGAR; the notebook therefore tries a local copy and this repository first.

Earnings-call transcripts are copyrighted by their publishers and are not included. Participants who hold a licence can drop a transcript into this folder and register it in the `DOCS` list in the notebook.
