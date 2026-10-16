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

## Corrections

If we misread a document or a release has moved, open an issue here or
write to support@wavefieldresearch.com with the link. We will recheck and
note corrections in the report.

## License and citation

Data released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Cite as: Wavefield Research, "2026 Midterm Poll Transparency Report,"
October 2026, https://wavefieldresearch.com/midterm-poll-transparency
