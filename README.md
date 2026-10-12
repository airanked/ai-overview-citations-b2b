---
license: cc-by-4.0
pretty_name: AI Overview Citations for B2B Software Queries (US, Oct 2026, Wave 1)
language:
- en
size_categories:
- n<1K
task_categories:
- text-classification
tags:
- google-ai-overviews
- ai-search
- citations
- b2b-software
- seo
- geo
- generative-engine-optimization
configs:
- config_name: default
  data_files: ai-overview-citations-b2b.csv
---

# AI Overview Citations for B2B Software Queries (US, Oct 2026, Wave 1)

Which sources do Google AI Overviews cite for B2B software buying queries? This dataset logs every source Google linked in the AI Overview for 150 US buyer searches across 10 B2B software categories.

Full report: https://airanked.ai/research/ai-overview-citations-b2b

Creator: AI Ranked Editorial. License: CC BY 4.0.

## Headline numbers

- 150 queries written, 15 in each of 10 categories.
- 132 queries measured (a current US Ahrefs SERP snapshot existed). 17 had no US snapshot and 1 had only a February 2024 snapshot; both groups are excluded from all rates.
- An AI Overview appeared on 122 of 132 measured queries (92.4%).
- 742 citations across those 122 AI Overviews.
- Software vendors' own sites earned 44.1% of citations. YouTube, Reddit and other forums took 30.9%. Review and listing sites took 5.0%.
- On a 40 query sample, 86 of 300 cited URLs (28.7%) also ranked in the organic top 10 of the same snapshot.
- Ahrefs snapshot dates: 28 August to 10 October 2026 (median 30 September). Collected through the API on 12 October 2026.

## Files

- `ai-overview-citations-b2b.csv`: 782 data rows. 742 citation rows, 12 flagged rows (`carousel_mismatch`, excluded from every number in the report) and 28 status rows for queries without an AI Overview or without a usable snapshot.

## Columns

- `query`: the search query.
- `category`: one of 10 B2B software categories (CRM, Project management, HR/payroll, Accounting, Cybersecurity, Marketing automation, BI/analytics, Customer support, Developer tools/DevOps, Sales engagement).
- `intent`: query pattern: `best`, `best_smb`, `industry`, `vs`, `top`, `alternatives`.
- `aio_present`: 1 if an AI Overview was present, 0 if the snapshot had none, empty if there was no usable snapshot.
- `citation_rank`: order of the citation in Ahrefs' record of the AI Overview.
- `url`: cited URL.
- `domain`: registrable domain of the cited URL.
- `title`: source title as recorded.
- `dr`: Ahrefs Domain Rating of the domain, read on 12 October 2026.
- `source_type`: hand classification of the domain (Software vendors, YouTube, Publishers and media, Reddit, forums and social, Agencies and consultants, Review and listing sites, Other).
- `excluded_flag`: empty for counted citations; `carousel_mismatch` for the 12 excluded links; `status:no_aio`, `status:no_snapshot` or `status:stale_snapshot_2024-02-27` for status rows.
- `ahrefs_update_date`: date of the Ahrefs SERP snapshot.

## Method

We wrote 150 buyer intent queries, 15 for each of 10 B2B software categories. Each category mixes six patterns: "best X software", "best X for small business", X for an industry or company size, "X vs Y" with two well known vendors, "top X tools" and "alternatives to [vendor]".

For each query we called the Ahrefs API v3 serp-overview endpoint with country US, filtered to AI Overview rows. An ai_overview row means an AI Overview was present; each ai_overview_sitelink row is one cited source. When the filtered call returned nothing, a second call for organic results separated "no AI Overview" from "no snapshot".

Cleaning: duplicate URLs inside the same AI Overview were removed (YouTube links differing only by timestamp or language count once); three Google redirect links were assigned to the domain named in the source title; 12 product list links whose titles name a vendor while the URL points to an unrelated page were flagged and excluded; domains are registrable domains. Each of the 310 cited domains was classified by hand into one source type. For the organic overlap, 4 AI Overview queries per category (40 total) were compared against the organic results in the top 10 positions of the same snapshot.

## Limitations

- One snapshot per query; AI Overviews change between searches and days, and snapshot dates vary by up to six weeks.
- US only, one location setting.
- Citation counts are a floor: 42 AI Overviews show exactly three sources, which suggests the collapsed view.
- Citation order is Ahrefs' order and may not match on-screen order on every device.
- The query set is ours and is not weighted by search volume.
- Source type classification is a judgment call; the CSV includes the type for every domain so you can reclassify.
- Domain Rating is current, not historical.
- The organic overlap covers 40 of the 122 AI Overview queries.
- This is wave 1; later waves will repeat the same queries.

## Citation

AI Ranked Editorial. "AI Overview Citations for B2B Software Queries (US, Oct 2026, Wave 1)" [Data set]. Zenodo. DOI: 10.5281/zenodo.23311409 (https://doi.org/10.5281/zenodo.23311409)

Report: AI Ranked Editorial. "Which sources do Google AI Overviews cite for B2B software queries?" AI Ranked, October 12, 2026. https://airanked.ai/research/ai-overview-citations-b2b

## License

Creative Commons Attribution 4.0 International (CC BY 4.0). Reuse freely with credit and a link to https://airanked.ai/research/ai-overview-citations-b2b
