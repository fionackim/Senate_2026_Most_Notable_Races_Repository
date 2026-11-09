# Campaign Fundraising and Spending in 2026 Senate Races

## Research question

How did reported campaign fundraising and spending compare among 2026 U.S. Senate candidates in Iowa, Michigan, Ohio and Texas?

## Project overview

This project uses Federal Election Commission (FEC) data to compare campaign receipts and disbursements for Senate candidates in four selected states.

The dataset includes candidates with FEC financial records for the 2026 election cycle. It includes primary candidates as well as general-election candidates, so it does not represent only the final November candidates in each state.

Ohio's 2026 Senate race was a special election to fill a vacant seat. The other states in this project held regularly scheduled Senate elections.

## Data

- **Source:** [FEC OpenFEC API](https://api.open.fec.gov/developers/)
- **Endpoint:** `/v1/candidates/totals/`
- **Election cycle:** 2026
- **Office:** U.S. Senate
- **States:** Iowa, Michigan, Ohio and Texas
- **Collected:** November 8, 2026
- **Records after cleaning:** 94
  - Iowa: 12
  - Michigan: 25
  - Ohio: 16
  - Texas: 41
- **Sample in the repository:** `data/sample/sample_clean.csv`, with three records per state

The FEC's `receipts` field reports money received by a campaign. `disbursements` reports campaign spending. These figures describe candidate campaigns and do not include all spending by outside groups, such as independent expenditures by Super PACs.

## Collection and cleaning

The notebook collects candidate financial totals from the FEC API for the 2026 Senate cycle in the four selected states. Requests use a descriptive User-Agent and pause between pages.

The raw API response and full cleaned dataset are saved locally. The repository contains the notebook and a 12-row sample of the cleaned data. The full raw response is excluded because it includes unnecessary fields, including candidate address information.

## Analysis plan

I will compare reported receipts and disbursements by state and party, identify candidates with the highest reported totals, and compare receipts with disbursements.

These figures represent the reports available when the data was collected. They may not reflect each candidate's final election-cycle totals, and different candidates' reports may cover different time periods.

## Data dictionary

| Field | Meaning |
|---|---|
| `candidate_id` | FEC identifier for the candidate |
| `candidate_name` | Candidate name as listed by the FEC |
| `party_code` | FEC party abbreviation |
| `party_name` | Full party name reported by the FEC |
| `state` | State abbreviation for the Senate race |
| `office` | Federal office code; `S` means Senate |
| `receipts` | Total campaign receipts reported for the 2026 cycle |
| `disbursements` | Total campaign spending reported for the 2026 cycle |
| `cash_on_hand` | Campaign cash on hand at the end of the reported period |
| `debts_owed` | Debt reported as owed by the campaign committee |
| `coverage_start_date` | Start date of the financial reporting period |
| `coverage_end_date` | End date of the financial reporting period |
| `last_filing_date` | Date of the latest FEC filing shown |

## Limitations

FEC candidate totals cover candidates who registered and filed financial reports; they may not include every person who appeared on a ballot. The FEC notes that its tables may not immediately reflect the newest filings.

This project measures candidate campaign receipts and disbursements, not total election spending by all campaigns, parties and outside groups. Ohio's race was a special election, so its circumstances differ from the regularly scheduled Senate races in Iowa, Michigan and Texas.
