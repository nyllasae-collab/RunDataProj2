# 🏃 Colorado HS Track & XC Results Aggregator

A Python-based data pipeline that scrapes, deduplicates, and consolidates high school cross country and track & field results from [MileSplit](https://co.milesplit.com) into a structured, queryable dataset.

## The Problem

High school running results in Colorado exist in scattered, unstructured formats — raw text files, meet-specific pages, no unified API. There's no single place to query athlete performance across meets, compare results by school or grade, or analyze trends over a season. This project fixes that.

## What It Does

- Fetches meet performance data from the MileSplit API across multiple race events
- Filters results to active high school athletes (grades 9–12)
- Deduplicates entries across runs using athlete/meet/event signatures
- Outputs a clean, structured JSON dataset ready for analysis or front-end consumption

## Output Schema

Each record in `all_race_results.json` contains:

| Field | Description |
|---|---|
| `name` | Athlete full name |
| `grad_year` | Graduation year (used to infer grade level) |
| `school` | Team/school name |
| `time` | Performance mark |
| `place` | Finish place |
| `meet_name` | Name of the meet |
| `meet_year` | Season year |
| `event_name` | Event (e.g. "5000 Meters") |
| `division` | Meet division |
| `gender` | Athlete gender |
| `meet_id` | MileSplit meet identifier |
| `athlete_id` | MileSplit athlete identifier |

## Getting Started

**Requirements**
```
pip install requests
```

**Usage**

Add race URLs to the `race_urls` list in `scraper.py`, then run:

```bash
python scraper.py
```

Results are saved to `all_race_results.json`. Re-running the script appends new data and skips duplicates automatically — no results are overwritten.

## Roadmap

- [ ] Automated scheduling (run weekly during season, no manual URL additions)
- [ ] Expanded meet coverage across all Colorado regions
- [ ] Interactive UI for filtering, ranking, and comparing athletes
- [ ] Season-over-season performance tracking
- [ ] Simulated race scoring (head-to-head team matchups)

## Tech Stack

- **Python** — core scraping and data processing
- **MileSplit API** — data source
- **JSON** — lightweight structured storage (database migration planned)

---

*Built to solve a real gap in high school athletics data infrastructure. Open to contributions and meet URL submissions.*
