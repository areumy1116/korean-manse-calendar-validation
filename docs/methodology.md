# Methodology

## Purpose

This validation project examines how different Korean Manse (만세력) calculation rules can produce different Four Pillars charts near time boundaries.

The comparison is designed to answer:

> If the same date, time, and place are entered, how much can the resulting chart differ when the calculation rules are not identical?

It is **not** designed to rank websites or determine a single universally correct school of calculation.

## Test year and location

- Year: **2026**
- Location: **Seoul, Republic of Korea**
- Input location was held constant across all comparisons.

## Case selection

A total of **200 cases** were selected deliberately from boundary regions where disagreement is more likely.

### 1. Solar-term boundaries — 120 cases

Twelve monthly solar-term transition points were used:

- Minor Cold (小寒)
- Beginning of Spring (立春)
- Awakening of Insects (驚蟄)
- Pure Brightness (清明)
- Beginning of Summer (立夏)
- Grain in Ear (芒種)
- Minor Heat (小暑)
- Beginning of Autumn (立秋)
- White Dew (白露)
- Cold Dew (寒露)
- Beginning of Winter (立冬)
- Major Snow (大雪)

For each transition, cases were taken at:

- 2 hours before
- 1 hour before
- 30 minutes before
- 10 minutes before
- 1 minute before
- 1 minute after
- 10 minutes after
- 30 minutes after
- 1 hour after
- 2 hours after

12 transitions × 10 offsets = **120 cases**.

### 2. Zi-hour / day-boundary cases — 40 cases

Forty cases were selected around **23:00 through midnight** across four dates in different seasons.

This region is especially sensitive because several rules may interact:

- whether 子時 begins at 23:00
- whether the day pillar changes at 23:00 or 00:00
- whether the hour pillar is calculated from corrected or uncorrected time
- whether fixed correction, local longitude, or true solar time is used

### 3. Ordinary hour-pillar boundaries — 40 cases

Forty additional cases were selected around ordinary two-hour branch boundaries.

These were used to isolate hour-pillar differences away from the day-change boundary.

## Comparison rules

The same date, time, and Seoul location were applied to **10 published calculation-rule sets**, anonymized as A through J in the original study.

The comparison focused on the resulting:

- year pillar
- month pillar
- day pillar
- hour pillar
- number of distinct full-chart outputs

The services/rules were not named because the study was about **rule differences**, not a public accuracy ranking.

## Aggregate findings

Across all 200 cases:

- 111 cases produced one identical chart across all 10 rule sets.
- 58 cases produced two distinct charts.
- 30 cases produced three distinct charts.
- 1 case produced four distinct charts.
- 89 cases had at least one disagreement.
- All 89 disagreement cases included an hour-pillar difference.
- 31 cases also included a day-pillar difference.

By category:

| Category | Total | Disagreement |
|---|---:|---:|
| Solar-term boundary | 120 | 39 |
| 23:00–00:00 / Zi-hour boundary | 40 | 33 |
| Ordinary hour-pillar boundary | 40 | 17 |

## Important interpretation constraint

The observed **44.5% disagreement rate** must not be treated as a general probability that two Manse calendars will disagree.

This sample was intentionally concentrated around unstable boundary times. A random sample of ordinary birth times would be expected to produce a different rate.

## Representative high-disagreement case

For **2026-02-11 23:45 in Seoul**, the 10 rule sets produced four distinct full charts:

- 丙午 庚寅 丙辰 己亥 — 4 rule sets
- 丙午 庚寅 丙辰 戊子 — 3 rule sets
- 丙午 庚寅 丁巳 庚子 — 2 rule sets
- 丙午 庚寅 丙辰 庚子 — 1 rule set

This case illustrates how time correction and day-boundary handling can interact.

## Related full-year validation

A separate woori.to study generated every minute of 2026:

- Start: 2026-01-01 00:00
- End: 2026-12-31 23:59
- Total timestamps: **525,600**

That study was used to test implementation mistakes and sensitivity around time boundaries under the site's own calculation rules.

## Source articles

- https://woori.to/entry/다른-만세력-사이트-10곳에-똑같은-경계시간-200개를-넣어봤습니다
- https://woori.to/entry/직접-만세력을-만들면서-실제로-틀렸던-계산-10가지
- https://woori.to/

## Raw-data policy

The full 200-row case table should only be committed from the original test data.

It should **not** be recreated by guessing timestamps from the published aggregate results. This repository therefore separates verified aggregates from raw data until the original source table is available.
