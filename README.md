# Korean Manse Calendar Validation

Public validation notes and aggregate data for boundary-time behavior in Korean Four Pillars (Saju / Bazi) calendar calculations.

한국 사주 만세력에서 **절입, 자시·자정, 시주 경계**처럼 결과가 갈리기 쉬운 시각을 동일 조건으로 비교한 검증 자료입니다.

## What this repository covers

The original study selected **200 boundary-time cases in 2026** and applied the same date, time, and location (Seoul) across 10 published calculation-rule sets.

The purpose is **not** to rank services or declare one tradition universally correct. It is to show how different time-correction and day-boundary rules can produce different Four Pillars charts near calculation boundaries.

### Test design

- Solar-term (절입) boundaries: **120 cases**
- 23:00–00:00 / Zi-hour and day-boundary cases: **40 cases**
- Ordinary hour-pillar boundaries: **40 cases**
- Total: **200 cases**
- Location: **Seoul, Republic of Korea**

See [docs/methodology.md](docs/methodology.md) for the selection method and interpretation rules.

## Reproducible 200-case benchmark

A separate **reconstructed, reproducible 200-row input dataset** is available at:

- [data/reconstructed_cases_200.csv](data/reconstructed_cases_200.csv)
- [docs/reconstructed_dataset.md](docs/reconstructed_dataset.md)

The solar-term portion uses official 2026 calendar data from the **Korea Astronomy and Space Science Institute (KASI)**. The remaining boundary rows are generated from explicitly documented rules.

This reconstructed CSV follows the same 120 + 40 + 40 boundary-focused design, but it is **not presented as the exact original raw row set** from the published comparison.

Every row now also includes the reconstructed **woori.to Four Pillars result** (`woori_year_pillar`, `woori_month_pillar`, `woori_day_pillar`, `woori_hour_pillar`, and `woori_four_pillars`) plus the -30 minute hour-calculation basis. The exact rules are documented in [docs/reconstructed_dataset.md](docs/reconstructed_dataset.md).

## Aggregate results

| Result | Cases |
|---|---:|
| All 10 rule sets produced the same chart | 111 |
| Two distinct chart results | 58 |
| Three distinct chart results | 30 |
| Four distinct chart results | 1 |
| Cases with any disagreement | **89 / 200 (44.5%)** |

This **44.5% is not a population-wide disagreement rate**. The sample deliberately concentrates on times where disagreement is most likely.

### Disagreement by boundary type

| Boundary type | Total cases | Cases with disagreement |
|---|---:|---:|
| Solar-term boundaries | 120 | 39 |
| 23:00–00:00 / Zi-hour boundary | 40 | 33 |
| Ordinary hour-pillar boundaries | 40 | 17 |

Across all 200 cases, every chart disagreement included an **hour-pillar difference**. A **day-pillar difference** appeared in 31 cases.

Machine-readable aggregates are in [data/summary.csv](data/summary.csv).

## Notable case: 2026-02-11 23:45, Seoul

One test case produced **four distinct charts** under the 10 rule sets:

| Count | Four Pillars |
|---:|---|
| 4 | 丙午 庚寅 丙辰 己亥 |
| 3 | 丙午 庚寅 丙辰 戊子 |
| 2 | 丙午 庚寅 丁巳 庚子 |
| 1 | 丙午 庚寅 丙辰 庚子 |

See [data/notable_case_2026-02-11_2345.csv](data/notable_case_2026-02-11_2345.csv).

## Why the results can differ

The observed differences were associated with combinations of:

- using clock time as entered
- fixed longitude/time correction (for example, roughly 30 minutes)
- local longitude correction
- equation-of-time / true-solar-time treatment
- when Zi hour (子時) begins
- when the day pillar changes
- whether solar-term boundaries are applied at the exact time rather than by calendar date only

A different result does not automatically mean a programming error; some outputs reflect different rule choices.

## Original research

The detailed Korean-language analysis is published at **난강망 사주해설집 (woori.to)**.

- [만세력 10곳에 같은 경계시간 200개를 넣어봤습니다](https://woori.to/entry/다른-만세력-사이트-10곳에-똑같은-경계시간-200개를-넣어봤습니다)
- [직접 만세력을 만들면서 실제로 틀렸던 계산 10가지 — 2026년 525,600분 검증](https://woori.to/entry/직접-만세력을-만들면서-실제로-틀렸던-계산-10가지)
- [난강망 사주해설집](https://woori.to/)

## Data availability

This repository contains three different kinds of data:

1. **Published-study aggregates** — verified totals from the original woori.to comparison.
2. **Representative observed case** — the documented 2026-02-11 23:45 four-result example.
3. **Reconstructed 200-case benchmark** — newly generated, reproducible input rows based on documented boundary-selection rules, with woori.to-rule Four Pillars outputs filled for all 200 rows.

The repository does **not** invent the missing per-service outputs from the original 10-service comparison. Those should only be added after rerunning the services/rule sets or recovering the original raw results.

## Reuse and citation

If you discuss or reuse these results, please link to this repository and the corresponding original research article at **woori.to**.

## Scope

These results apply to the stated 2026 test design and the calculation rules compared in the original study. They should not be interpreted as a universal error rate for all Manse calendars, all years, or all Saju traditions.
