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

This repository currently publishes **verified aggregate results and a documented representative case** from the original study.

The complete 200-row raw case table is intentionally **not reconstructed from memory or inferred values**. It should be added only from the original source data so the repository remains reproducible and accurate.

## Reuse and citation

If you discuss or reuse these results, please link to this repository and the corresponding original research article at **woori.to**.

## Scope

These results apply to the stated 2026 test design and the calculation rules compared in the original study. They should not be interpreted as a universal error rate for all Manse calendars, all years, or all Saju traditions.
