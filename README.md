# John Barreto

**Independent natural gas research · Henry Hub · Portugal**

I study how weather, storage and the forward curve shape the North American natural gas market. I publish interactive tools, source data and methods so readers can inspect the evidence behind a result and understand its limits.

## Start with a question

- **Does weather improve a storage estimate?** Read the [storage research note](https://neurax-jb.github.io/natural-gas-research-notes/lab/research/storage-weather.html) and inspect the [storage dashboard](https://neurax-jb.github.io/henry-hub-storage-forecaster/).
- **What changed for the same delivery month?** Compare dates in the [futures curve explorer](https://neurax-jb.github.io/henry-hub-futures-curve/).
- **What could a fixed-price share do to a factory's gas bill?** Try the [industrial cost simulator](https://neurax-jb.github.io/industrial-gas-cost-simulator/), with its delivery-price assumptions shown separately.

## A result you can examine

In a **retrospective storage nowcast replay**, adding observed weather reduced the average absolute weekly miss by **10.00 billion cubic feet (Bcf)** against a five-year seasonal median.

| Evaluation | Observed-weather model | Seasonal median |
| :--- | ---: | ---: |
| Mean absolute error (Bcf) | 20.50 | 30.50 |
| Identical weekly evaluation dates | 463 | 463 |

**Period:** 5 January 2018–13 November 2026. **Relative error reduction:** 32.8%. MAE is the average size of a miss, regardless of its direction; lower is better. The values above describe this recorded sample, not an expected future error.

The replay uses current-vintage observations. Original historical publication timing is not established for every input, so this is **not verified performance from forecasts issued before each EIA release**. There were **zero completed scored live forecasts** in the 23 November 2026 snapshot. The reported interval covered 78.2% of the evaluated observations; that is measured coverage, not a guarantee.

Inspect the frozen [weekly results](https://github.com/NeuraX-JB/henry-hub-storage-forecaster/blob/30148e34f458c2caa057ce36472e3a457f04064f/lab/storage/backtest.csv), [model code](https://github.com/NeuraX-JB/henry-hub-storage-forecaster/blob/30148e34f458c2caa057ce36472e3a457f04064f/lab/storage/model.py), and [recorded model state](https://github.com/NeuraX-JB/henry-hub-storage-forecaster/blob/30148e34f458c2caa057ce36472e3a457f04064f/lab/storage/state.json). The [project instructions](https://github.com/NeuraX-JB/henry-hub-storage-forecaster#readme) explain how to run the tests and reproduce the replay.

## Research tools and evidence

These are research snapshots and historical scenarios. Each repository contains its own code and documentation; its demo serves that repository's reviewed version. The original [research lab](https://neurax-jb.github.io/Henry-Hub-Futures-Curve-Explorer-How-the-Natural-Gas-Market-prices-winter/lab/) remains the separate home of ongoing data refreshes.

| Project | Question it helps investigate | Evidence type | Open |
| :--- | :--- | :--- | :--- |
| Storage forecaster | Does observed weather improve a seasonal storage estimate? | Historical replay; live record not established | [Demo](https://neurax-jb.github.io/henry-hub-storage-forecaster/) · [Code](https://github.com/NeuraX-JB/henry-hub-storage-forecaster) |
| Weather revision monitor | Where did demand-related temperature exposure change between forecast runs? | Archived GFS comparisons on common valid dates | [Demo](https://neurax-jb.github.io/natural-gas-weather-monitor/) · [Code](https://github.com/NeuraX-JB/natural-gas-weather-monitor) |
| Futures curve explorer | How did the market reprice the same delivery contracts? | Historical curves and reconstructed examples | [Demo](https://neurax-jb.github.io/henry-hub-futures-curve/) · [Code](https://github.com/NeuraX-JB/henry-hub-futures-curve) |
| Industrial gas cost simulator | How do procurement assumptions change historical fuel costs? | Illustrative Henry Hub cost scenarios | [Demo](https://neurax-jb.github.io/industrial-gas-cost-simulator/) · [Code](https://github.com/NeuraX-JB/industrial-gas-cost-simulator) |
| Natural gas data API | How can storage, weather and price observations be joined consistently? | Static JSON/CSV datasets with source metadata | [Demo](https://neurax-jb.github.io/natural-gas-data-api/) · [Code](https://github.com/NeuraX-JB/natural-gas-data-api) |
| Research notes | What can the studies establish, and what remains untested? | Methods, findings and limitations | [Read](https://neurax-jb.github.io/natural-gas-research-notes/) · [Sources](https://github.com/NeuraX-JB/natural-gas-research-notes) |
