# Reconstructed 200-case benchmark

This file documents how `data/reconstructed_cases_200.csv` was generated.

## Important distinction

The CSV is a **newly reconstructed benchmark dataset**, not a claim that these are the exact original 200 raw rows used in the published woori.to comparison.

The goal is to provide a transparent, reproducible set of boundary-focused inputs that follows the same published design:

- 120 solar-term boundary cases
- 40 Zi-hour / day-boundary cases
- 40 ordinary hour-pillar boundary cases

## 1. Solar-term boundary cases (120)

The 12 monthly branch-changing solar terms for 2026 were taken from the Korea Astronomy and Space Science Institute (KASI) calendar data.

Source:
https://astro.kasi.re.kr/kor/life/post/calendarData?year=2026

For each term, ten offsets were generated:

- -120 minutes
- -60 minutes
- -30 minutes
- -10 minutes
- -1 minute
- +1 minute
- +10 minutes
- +30 minutes
- +60 minutes
- +120 minutes

12 × 10 = 120 cases.

## 2. Zi-hour / day-boundary cases (40)

Four seasonally separated dates were selected:

- 2026-02-11
- 2026-05-11
- 2026-08-11
- 2026-11-11

For each date, ten points were generated around 23:00 and midnight:

22:59, 23:00, 23:01, 23:10, 23:20, 23:30, 23:40, 23:50, 23:59, 00:00 on the following day.

4 × 10 = 40 cases.

The February 11 date was retained because the published study contains a notable 23:45 example on that date. The other dates are reconstructed benchmark choices.

## 3. Ordinary hour-pillar boundaries (40)

The same four seasonal dates were used.

Two ordinary branch boundaries were sampled on each date:

- 05:00
- 13:00

Five offsets were generated for each boundary:

- -10 minutes
- -1 minute
- exact boundary
- +1 minute
- +10 minutes

4 dates × 2 boundaries × 5 offsets = 40 cases.

## What the CSV does not contain

It does **not** fabricate outputs from the 10 compared Manse services.

Those result columns should only be added after the services/rule sets are actually rerun or the original raw output table is recovered.

## Total

120 + 40 + 40 = **200 reproducible input cases**.
