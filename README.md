# New York State Eviction Map

Interactive map of residential eviction filings by ZIP code across New York State, comparing New York City with the rest of the state.

**Live site:** https://chengren.github.io/nys-eviction/

Regional companion map (Albany, Rensselaer, Saratoga, Schenectady): https://chengren.github.io/capreg-evictions/

## What it shows

- NYC and the rest of the state side by side: filings, share of the state total, filing rates and case outcomes
- Monthly filings for NYC and outside NYC, with a draggable date range
- Eviction filings by ZIP code, as a count or as annual filings per 1,000 renter households, viewable statewide, for NYC or for outside NYC
- For each ZIP code: monthly filings, main court, case outcomes and a renter profile (rent, income, rent burden, poverty, unemployment, race and ethnicity of renter householders)
- Tables of ZIP codes and of all 76 courts

## Data

**Eviction filings.** NY State Unified Court System, deidentified landlord-tenant extract. In New York City it covers the Civil Court in all five boroughs plus the Harlem and Red Hook community justice centers. Outside NYC it covers 61 city courts and the Nassau and Suffolk district courts. Commercial cases are excluded. Only aggregated ZIP-by-month counts are published here; no case-level records.

**Renter profile.** American Community Survey 2020-2024 5-year estimates for ZIP Code Tabulation Areas, via the Census API.

## Coverage

NYC counts are complete. Outside NYC, town and village courts are not in the extract, so most suburban and rural ZIP codes appear as "no data" and statewide totals outside NYC are a floor, not a full count. Outside NYC, a ZIP code counts as covered when the courts in the extract recorded at least 100 residential filings there. ZIP codes that straddle a city line are partly undercounted.

Coverage also varies by county outside NYC. Suffolk's district court covers whole towns, while most counties have only a city court, so rates are not strictly comparable from one county to the next.

## Methods

- **NYC or outside NYC:** assigned by the county that contains most of the ZIP code
- **Rate:** filings in the selected window ÷ months × 12 ÷ renter households × 1,000. Area rates use renter households in covered ZIP codes only.
- **Tiers:** quartiles of the January 2022 to latest-month rate across covered ZIP codes statewide, fixed so a color means the same rate in every area and window
- **Small renter base:** ZIP codes with fewer than 500 renter households are flagged, because their rates are unstable
- **Income needed to afford rent:** median gross rent × 12 ÷ 0.30
- Months before January 2022 fall under New York's eviction moratorium and are partial.

## Files

```
index.html                  the page (D3.js, no build step)
data/eviction_state.json    filings and outcomes by ZIP code, region and court, by month
data/acs_zcta_ny.csv        ACS renter profile by ZCTA
data/zcta_geo.geojson       ZCTA boundaries (2020)
data/county_geo.geojson     county boundaries (2020)
```

## Run locally

The page loads files from `data/`, so open it through a local server rather than double-clicking:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Contact

Maintained by [@chengren](https://github.com/chengren), School of Social Welfare, University at Albany, SUNY.
