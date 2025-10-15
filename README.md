# Project 2 — Wide → Tidy Data Wrangling & Analysis (NYC)

This project practices tidying “wide” datasets and performing light quantitative analysis in Python/pandas. I work through three NYC datasets, reshape them between wide and tidy (long) forms, and summarize key patterns.

Datasets

NYC Motor Vehicle Collisions (Crashes)
Source (CSV endpoint): https://data.cityofnewyork.us/resource/h9gi-nx95.csv
Slice: Calendar year 2023
Focus: total persons injured by month × borough (wide), tidy back, borough shares, simple severity proxy.

NYC 311 Service Requests
Source (CSV endpoint): https://data.cityofnewyork.us/resource/erm2-nwe9.csv
Slice: Calendar year 2023
Focus: top complaint types, weekly trends for top-5 categories, noise share by borough, hour-of-day patterns.

NYC Restaurant Inspection Results
Source (CSV endpoint): https://data.cityofnewyork.us/resource/43nn-pn8j.csv
Slice: Last full 12 months
Focus: borough × grade counts (A/B/C) as a wide table, tidy back, A-rate by borough, monthly A-grade trends.

All pulls use Socrata query parameters ($select, $where, $order, $limit, $offset) embedded in the URL.

# What I did

 Load → Wide → Tidy:

 Built explicit wide matrices (e.g., month × borough, borough × grade, week × complaint_type).

 Melted back to tidy for grouping, rolling means, and ratio calculations.

# Summaries & checks:

Collisions: monthly injuries by borough, borough shares, injuries per 100 crashes (severity proxy), seasonality.

311: top complaint mix, weekly table for top-5, noise share by borough, busiest hours overall and by borough.

Inspections: A/B/C counts by borough (wide), A-rate per borough, monthly A-grade trend (rolling mean).

Robust field handling: current collisions schema uses number_of_* columns; the notebook auto-maps to handle both old/new names.

# Key highlights (from my runs)

Collisions (2023): A clear month × borough injury matrix; boroughs differ not just in volume but also injuries per 100 crashes, indicating different severity profiles.

311 (2023): Noise complaints dominate, especially evenings/weekends. Weekly series show holiday spikes, boroughs differ in category mix (e.g., helicopter noise in Manhattan, blocked driveway in lower-density areas).

Inspections (last 12 months): Manhattan & Staten Island show the highest A-grade share, Queens has a relatively higher C share. Borough differences in grade distributions are statistically meaningful.

Caveats: 311 reflects reported complaints, inspections depend on inspection timing, collisions data has missing boroughs and reporting artifacts.
