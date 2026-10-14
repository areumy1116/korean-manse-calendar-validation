# Korean Manse Calendar Validation

Validation notes and aggregate data on how Korean Four Pillars (Saju / Bazi) calendars behave at boundary times.

한국 사주 만세력에서 절입, 자시·자정, 시주 경계처럼 결과가 갈리기 쉬운 시각만 골라 같은 조건으로 넣어 보고, 어디서 얼마나 달라지는지 기록한 자료입니다.

## Why I made this

I started this while building my own Manse calendar. Every time I checked my output against existing services, the mismatches showed up in the same few places: right around a solar-term change, late at night near 23:00, and at the edge of an hour pillar. I wanted to know whether those mismatches were bugs or just different rules, so I stopped spot-checking and ran a proper comparison.

This is not a ranking of services. I don't think any single tradition gets to call itself the correct one. What I wanted to show is how much the chart can move depending on the time-correction and day-boundary rules a calculator picks.

## What was tested

I picked 200 boundary-time cases in 2026 and entered the same date, time, and location (Seoul) into 10 published calculation-rule sets.

| Boundary type | Cases |
|---|---|
| Solar-term (절입) boundaries | 120 |
| 23:00–00:00 / Zi-hour and day boundary | 40 |
| Ordinary hour-pillar boundaries | 40 |
| **Total** | **200** |

How the cases were chosen and how I read the results is in [`docs/methodology.md`](docs/methodology.md).

## Reproducible 200-case benchmark

If you want to run your own calculator against the same kind of inputs, use these:

- [`data/reconstructed_cases_200.csv`](data/reconstructed_cases_200.csv)
- [`docs/reconstructed_dataset.md`](docs/reconstructed_dataset.md)

The solar-term rows come from the [2026 calendar data](https://astro.kasi.re.kr/kor/life/post/calendarData?year=2026) published by the Korea Astronomy and Space Science Institute (KASI). The other rows are generated from rules written out in the doc, so anyone can rebuild them.

One thing to be clear about: this CSV keeps the same 120 + 40 + 40 split as the original study, but it is a reconstruction. It is not the exact raw row set from the published comparison.

Each row also carries the woori.to result (`woori_year_pillar`, `woori_month_pillar`, `woori_day_pillar`, `woori_hour_pillar`, `woori_four_pillars`) and the −30 minute basis used for the hour calculation. The details are in [`docs/reconstructed_dataset.md`](docs/reconstructed_dataset.md).

## Results

| Result | Cases |
|---|---|
| All 10 rule sets gave the same chart | 111 |
| Two different charts | 58 |
| Three different charts | 30 |
| Four different charts | 1 |
| Any disagreement | 89 / 200 (44.5%) |

Please don't quote 44.5% as "how often Manse calendars disagree." I deliberately loaded the sample with the times where disagreement is most likely. On an ordinary afternoon birth time, almost every calculator will agree.

### By boundary type

| Boundary type | Total | With disagreement |
|---|---|---|
| Solar-term boundaries | 120 | 39 |
| 23:00–00:00 / Zi-hour boundary | 40 | 33 |
| Ordinary hour-pillar boundaries | 40 | 17 |

The Zi-hour band is the one that stood out to me. 33 out of 40 is far worse than I expected going in. Solar-term cases, which I assumed would be the messiest, actually held together better.

Every single disagreement in the 200 cases involved the hour pillar. The day pillar differed in 31 of them.

Aggregates in machine-readable form: [`data/summary.csv`](data/summary.csv).

## The case that split four ways: 2026-02-11 23:45, Seoul

| Rule sets | Four Pillars |
|---|---|
| 4 | 丙午 庚寅 丙辰 己亥 |
| 3 | 丙午 庚寅 丙辰 戊子 |
| 2 | 丙午 庚寅 丁巳 庚子 |
| 1 | 丙午 庚寅 丙辰 庚子 |

Year and month never moved. Everything happened in the day and hour. My reading of it: the four sets that returned 己亥 corrected the clock time far enough back that 23:45 never reached Zi hour. The two sets with 丁巳 庚子 switch the day at the start of Zi hour. The single 丙辰 庚子 result keeps the day as 丙辰 but takes the hour stem from the next day, which is the 야자시 approach. The 丙辰 戊子 group keeps both on the current day.

So one birth time, four charts, and you could defend most of them depending on which school you follow. That's exactly why I think a calculator should tell users which rule it's using instead of just printing a chart.

Raw data: [`data/notable_case_2026-02-11_2345.csv`](data/notable_case_2026-02-11_2345.csv).

## Where the differences come from

The splits I saw traced back to some mix of these choices:

- taking the clock time as entered, with no correction
- applying a fixed correction (around 30 minutes for Seoul)
- correcting by local longitude
- applying the equation of time / true solar time
- where Zi hour (子時) is taken to start
- when the day pillar rolls over
- whether a solar-term change is applied at its exact minute or just by calendar date

A different chart doesn't automatically mean someone has a bug. In a lot of these cases the code is doing exactly what it was designed to do. The design choices are just different.

## Original research

The full write-up in Korean is on [난강망 사주해설집 (woori.to)](https://woori.to/):

- [만세력 10곳에 같은 경계시간 200개를 넣어봤습니다](https://woori.to/entry/다른-만세력-사이트-10곳에-똑같은-경계시간-200개를-넣어봤습니다)
- [직접 만세력을 만들면서 실제로 틀렸던 계산 10가지 — 2026년 525,600분 검증](https://woori.to/entry/직접-만세력을-만들면서-실제로-틀렸던-계산-10가지)

## What data is in here

There are three kinds, and they shouldn't be mixed up:

1. **Published-study aggregates**: the verified totals from the original woori.to comparison.
2. **One observed case**: the 2026-02-11 23:45 example above, documented as it came out.
3. **Reconstructed 200-case benchmark**: new, reproducible input rows built from the documented selection rules, with woori.to-rule outputs filled in for all 200.

I have not filled in per-service outputs for the original 10-service comparison, and I won't make them up. They'll go in only after the services are rerun or the original raw results are recovered.

## Reuse and citation

If you use or discuss these results, please link both this repository and the [original article on woori.to](https://woori.to/entry/다른-만세력-사이트-10곳에-똑같은-경계시간-200개를-넣어봤습니다).

## Scope

Everything here applies to the 2026 test design and the rule sets compared in the original study. It isn't an error rate for all Manse calendars, all years, or all Saju traditions.
