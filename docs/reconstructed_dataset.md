# Reconstructed 200-case benchmark

This file documents how `data/reconstructed_cases_200.csv` was generated and how the **woori.to result columns** were calculated.

## Important distinction

The CSV is a **newly reconstructed benchmark dataset**, not a claim that these are the exact original 200 raw rows used in the published woori.to comparison.

The goal is to provide a transparent, reproducible set of boundary-focused inputs that follows the same published design:

- 120 solar-term boundary cases
- 40 Zi-hour / day-boundary cases
- 40 ordinary hour-pillar boundary cases

The CSV now also contains a deterministic **woori.to-rule reconstruction** for each of the 200 rows.

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

Two nominal branch boundaries were sampled on each date:

- 05:00
- 13:00

Five offsets were generated for each boundary:

- -10 minutes
- -1 minute
- exact boundary
- +1 minute
- +10 minutes

4 dates × 2 boundaries × 5 offsets = 40 cases.

## woori.to result calculation

The following columns are calculated for every row:

- `woori_year_pillar`
- `woori_month_pillar`
- `woori_day_pillar`
- `woori_hour_pillar`
- `woori_four_pillars`
- `woori_hour_basis_kst`

### Year pillar

The year pillar changes at the exact **Beginning of Spring (立春 / 입춘)** time.

For 2026:

- through 2026-02-04 05:01 KST: **乙巳**
- from 2026-02-04 05:02 KST: **丙午**

### Month pillar

The month pillar changes at the exact monthly solar-term boundary rather than at 00:00 on the civil calendar date.

The 2026 boundary instants come from the KASI calendar data.

### Day pillar

The day pillar follows the civil date and is **not shifted by the -30 minute hour correction**.

The day-cycle implementation is anchored to the KASI-published reference:

- 2026-02-17 = **壬戌**

All other 2026 day pillars are obtained by sexagenary-cycle day offsets from that reference.

### Hour pillar

For the hour pillar only, the site applies a fixed **-30 minute correction** to the entered clock time.

The corrected time determines the two-hour earthly-branch interval.

The hour stem is then derived from the **unadjusted civil-date day stem** using the standard Five Rats rule (五鼠遁):

- 甲 / 己 day → 甲子 start
- 乙 / 庚 day → 丙子 start
- 丙 / 辛 day → 戊子 start
- 丁 / 壬 day → 庚子 start
- 戊 / 癸 day → 壬子 start

The -30 minute correction is not propagated backward into the year, month, or day pillar.

## Cross-check

The published comparison includes a notable case:

**2026-02-11 23:45, Seoul**

Using the rules above:

- Year: 丙午
- Month: 庚寅
- Day: 丙辰
- Hour basis after -30 minutes: 23:15
- Hour: 戊子
- Result: **丙午 庚寅 丙辰 戊子**

That exact chart is one of the four observed outputs documented in the original comparison.

## What the CSV still does not contain

It does **not** fabricate outputs from the other 10 compared Manse services.

Those per-service result columns should only be added after the services/rule sets are actually rerun or the original raw output table is recovered.

## Total

120 + 40 + 40 = **200 reproducible input cases**, each now accompanied by one woori.to-rule Four Pillars result.
