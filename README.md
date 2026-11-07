# 2026 Midterm Poll Transparency Dataset

Data from the [2026 Midterm Poll Transparency Report](https://wavefieldresearch.com/midterm-poll-transparency)
by [Wavefield Research](https://wavefieldresearch.com): an audit of 141
publicly cited 2026 United States midterm poll documents against 8
disclosure elements adapted from
[AAPOR's Disclosure Standards](https://aapor.org/standards-and-ethics/disclosure-standards/).

## Headline findings

- Only 27% of readable poll documents disclose all 8 elements. The median is 6.
- The weakest element is the sampling frame: 43% of readable documents say
  where their respondents came from (voter file, named panel, RDD).
- 42% of the public citations lead to documents an automated reader cannot
  open: paywalls, bot walls, image-only PDFs, dead links, or login-walled
  tweets. These are coded as not assessed, never as nondisclosure.

## The data

`data/midterm-poll-transparency-data.csv`: one row per cited poll document
(141 rows). Columns:

| Column | Meaning |
|---|---|
| pollster | Pollster name as listed in the public record |
| race | Race the poll was cited for |
| field_dates | Field dates as listed |
| source_url | The document the public citation reaches |
| doc_type | pollster_release, news_article, aggregator, tweet, or other |
| reachable | True if the document could be read in full |
| sponsor, dates, n, population, mode, frame, weighting, moe | 1 = stated in the document; 0 = document read, element absent; empty = not assessed |

## Method in brief

Corpus: every poll listed in the polling tables of the Wikipedia pages for
40 races (20 Senate, 20 governor) as of October 15, 2026, filtered to polls
fielded in 2026 that carry a public source citation. Unit of analysis: the
document each citation reaches, which is what a reader following the public
trail actually finds. Where one poll is cited through more than one
document, each document is coded separately, since each is its own
disclosure act. Full methodology, coding conventions, and limits are in the
[report](https://wavefieldresearch.com/midterm-poll-transparency).

This audit measures transparency, not polling accuracy. A poll can disclose
nothing and still be well executed; the point of disclosure is that readers
should not have to take that on faith.

## November 2026 human-reader re-check

`data/reaudit-human-reader-nov2026.csv`: one row per originally
unreachable document (59 rows). On November 6, 2026 we re-visited every
blocked citation in an ordinary consumer browser session with no
accounts, subscriptions, or payments. Columns:

| Column | Meaning |
|---|---|
| row | Row index of the document in the main CSV (0-based) |
| recheck_category | bot_wall, js_shell, plain_fetch_ok, tweet_public, aggregator_no_text, paywall, bot_toll, rate_limited_unverified, dead, homepage_only |
| human_reachable | 1 if the document opened in full for a human reader |
| h_sponsor ... h_moe | Element codes under the human-reader standard (same 1/0/empty scheme as the main CSV) |
| h_score | Count of disclosed elements, 0-8 |
| note | What we found at the URL |

Headline: 42 of 59 opened for a human reader and 41 could be coded in
full. Under the human-reader standard the unreachable share of the
public record falls from 42% to 12% (17 of 141), while the disclosure
picture barely moves: 25% of all fully readable documents carry all 8
elements, versus 27% under the automated-reader standard. The main CSV
is unchanged; the original `reachable` column still describes the
automated reader at audit time (October 2026), and categories in the
re-check describe November 2026 (link health changes in both
directions).

## Note on SoCal Strategies (November 7, 2026)

The main CSV contains one SoCal Strategies release (Michigan Senate,
fielded July 28 to 30, 2026), coded 8 of 8 from the firm's Substack in
October 2026. After our audit window, FiftyPlusOne and the Washington
Post publicly questioned the authenticity of some SoCal Strategies
polls, and the firm took its website and Substack offline on October
22, 2026, which also removed the document we coded (the cited URL now
returns 404). Nothing has been proven about this specific poll. The
row stays as coded because this dataset records what the cited
document disclosed when we read it; disclosure coding says nothing
about whether the survey behind a document was conducted as described.

## Corrections

If we misread a document or a release has moved, open an issue here or
write to support@wavefieldresearch.com with the link. We will recheck and
note corrections in the report.

## License and citation

Data released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Cite as: Wavefield Research, "2026 Midterm Poll Transparency Report,"
October 2026, https://wavefieldresearch.com/midterm-poll-transparency
