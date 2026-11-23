# Portfolio review: publication and verification results

**John Barreto · Review date: 23 November 2026**  
**Hosted check audit updated: 23 November 2026, 22:26:36 UTC**

The six project editions below have been published. Their final `main` heads were read back and matched the reviewed commits. All **six research-validation workflows** and **six GitHub Pages deployment workflows** completed successfully for those exact commits.

The executable project suites passed **90 automated test cases**. The research-notes project additionally passed its static-page synchronization and saved-evidence arithmetic checks. These results accompany the [100 findings and fixes](AUDIT_100.md); they do not establish live forecast skill or universal browser compatibility.

## Published editions

| Project | Deployed project | Verified final commit |
| :--- | :--- | :--- |
| Henry Hub Storage Forecaster | [Open storage](https://neurax-jb.github.io/henry-hub-storage-forecaster/) | [4f884fe41be2f2a88a023f78a9a539110df8953d](https://github.com/NeuraX-JB/henry-hub-storage-forecaster/commit/4f884fe41be2f2a88a023f78a9a539110df8953d) |
| Natural Gas Weather Monitor | [Open weather](https://neurax-jb.github.io/natural-gas-weather-monitor/) | [23c19cce1a43177e18960ad71663bcea1f94e58e](https://github.com/NeuraX-JB/natural-gas-weather-monitor/commit/23c19cce1a43177e18960ad71663bcea1f94e58e) |
| Henry Hub Futures Curve | [Open curve explorer](https://neurax-jb.github.io/henry-hub-futures-curve/) | [23afbe7e295a5b262f820e72491040153acc6f73](https://github.com/NeuraX-JB/henry-hub-futures-curve/commit/23afbe7e295a5b262f820e72491040153acc6f73) |
| Industrial Gas Cost Simulator | [Open simulator](https://neurax-jb.github.io/industrial-gas-cost-simulator/) | [f16dd2fb61464c2e59528b764a542eb6d1473a56](https://github.com/NeuraX-JB/industrial-gas-cost-simulator/commit/f16dd2fb61464c2e59528b764a542eb6d1473a56) |
| Natural Gas Data API | [Open API project](https://neurax-jb.github.io/natural-gas-data-api/) | [896d514361aea9f81400616d9b1d70be64322678](https://github.com/NeuraX-JB/natural-gas-data-api/commit/896d514361aea9f81400616d9b1d70be64322678) |
| Natural Gas Research Notes | [Read publications](https://neurax-jb.github.io/natural-gas-research-notes/) | [c53220435f8899e4fa39bab0a1b38e52695b5e72](https://github.com/NeuraX-JB/natural-gas-research-notes/commit/c53220435f8899e4fa39bab0a1b38e52695b5e72) |

The storage edition includes the final wording correction: its target is a change in working-gas stocks, which can include reclassifications. The display uses stock increase/decrease labels and identifies Bcf on all numeric weekly-table columns. A subsequent HTML-only fix requests `app.js?v=56286dca7cef`, using the first 12 SHA-256 characters of the corrected script, after live review exposed a cached older label. Storage's final CI and Pages runs were rechecked successfully at **23 November 2026, 22:24:05 UTC**. These clarifications remain within findings 23 and 27; they do not add findings or alter numerical results.

The curve commit includes a contrast correction identified during the live screenshot review: its historical-snapshot label now uses #d2e8df on the #102e30 hero. The calculated foreground/background contrast is **11.23:1**, compared with **1.87:1** before the correction. Layout, behavior and frozen data are unchanged; the 12 regression cases and both hosted workflows passed for the updated commit. This color-pair check is not a whole-page accessibility certification.

## Hosted validation and deployment

Each link identifies the successful run for the commit in the table above. Successful deployment means that GitHub's Pages workflow completed; the separate browser review records which resulting interfaces were actually exercised.

| Project | Verify research snapshot | Pages build and deployment |
| :--- | :--- | :--- |
| Storage | [Success · 45279208640](https://github.com/NeuraX-JB/henry-hub-storage-forecaster/actions/runs/45279208640) | [Success · 45279207684](https://github.com/NeuraX-JB/henry-hub-storage-forecaster/actions/runs/45279207684) |
| Weather | [Success · 45277114463](https://github.com/NeuraX-JB/natural-gas-weather-monitor/actions/runs/45277114463) | [Success · 45277329004](https://github.com/NeuraX-JB/natural-gas-weather-monitor/actions/runs/45277329004) |
| Futures curve | [Success · 45279473481](https://github.com/NeuraX-JB/henry-hub-futures-curve/actions/runs/45279473481) | [Success · 45279472867](https://github.com/NeuraX-JB/henry-hub-futures-curve/actions/runs/45279472867) |
| Industrial simulator | [Success · 45277713791](https://github.com/NeuraX-JB/industrial-gas-cost-simulator/actions/runs/45277713791) | [Success · 45277905651](https://github.com/NeuraX-JB/industrial-gas-cost-simulator/actions/runs/45277905651) |
| Data API | [Success · 45277781096](https://github.com/NeuraX-JB/natural-gas-data-api/actions/runs/45277781096) | [Success · 45277960193](https://github.com/NeuraX-JB/natural-gas-data-api/actions/runs/45277960193) |
| Research notes | [Success · 45277921067](https://github.com/NeuraX-JB/natural-gas-research-notes/actions/runs/45277921067) | [Success · 45278045169](https://github.com/NeuraX-JB/natural-gas-research-notes/actions/runs/45278045169) |

## Automated test evidence

| Project | Passed cases | Suite composition and reproducible commands |
| :--- | ---: | :--- |
| Storage | 21 | 14 Python model/research-guard cases, 3 shared-data cases, 4 Node presentation regressions. [Command manifest](https://github.com/NeuraX-JB/henry-hub-storage-forecaster/blob/4f884fe41be2f2a88a023f78a9a539110df8953d/scripts/checks.json) |
| Weather | 19 | 12 Node engine cases, 4 Node page-controller cases, 3 Python archive-guard cases. [Command manifest](https://github.com/NeuraX-JB/natural-gas-weather-monitor/blob/23c19cce1a43177e18960ad71663bcea1f94e58e/scripts/checks.json) |
| Futures curve | 12 | 5 Node engine cases and 7 Node controller/chart cases. [Command manifest](https://github.com/NeuraX-JB/henry-hub-futures-curve/blob/23afbe7e295a5b262f820e72491040153acc6f73/scripts/checks.json) |
| Industrial simulator | 19 | 10 Node model cases, 6 Node page-controller cases, 3 Python source-rebuild cases. [Command manifest](https://github.com/NeuraX-JB/industrial-gas-cost-simulator/blob/f16dd2fb61464c2e59528b764a542eb6d1473a56/scripts/checks.json) |
| Data API | 19 | 12 Python API cases, 3 shared-data cases, 4 Node response-contract cases. [Command manifest](https://github.com/NeuraX-JB/natural-gas-data-api/blob/896d514361aea9f81400616d9b1d70be64322678/scripts/checks.json) |
| **Total** | **90** | Counted test cases across the five project suites. |

This count does not inflate individual assertions, JSON rows, checked links or note-table rows into additional test cases. The shared-data suite runs separately in storage and the API, so its three cases appear in each project's total; 90 is the aggregate suite count, not a claim of 90 unique test implementations.

The common validator also checks local HTML/Markdown/CSS destinations, strict JSON syntax and frozen-data SHA-256 hashes. CI uses Python 3.12 and Node.js 24, with each project's dependencies listed in `scripts/requirements-ci.txt`. From a checked-out project root:

```sh
python -m pip install -r scripts/requirements-ci.txt
python scripts/validate.py
```

The validation workflow is offline with respect to research inputs: it does not refresh source observations or generate a new research edition. Python weather-archive guard tests use only the standard library; they do not require a GRIB download, GDAL or NumPy.

### Research-notes checks outside the 90-case total

The [notes command manifest](https://github.com/NeuraX-JB/natural-gas-research-notes/blob/c53220435f8899e4fa39bab0a1b38e52695b5e72/scripts/checks.json) runs `python lab/research/render_notes.py --check`. It confirms that **four generated reading pages** match their Markdown sources. The pages are static and do not require JavaScript.

A separate read-only run of [check_evidence.py](https://github.com/NeuraX-JB/natural-gas-research-notes/blob/c53220435f8899e4fa39bab0a1b38e52695b5e72/lab/research/check_evidence.py) also passed:

- All **10 published storage table rows**, including the pooled result, agree with the unchanged **463-row replay** at the displayed precision.
- All **nine matched delivery-month price pairs** and their September-minus-June differences agree with the saved curve evidence.

The local arithmetic check used the preserved storage replay and bundled curve asset. The [frozen-evidence guide](https://github.com/NeuraX-JB/natural-gas-research-notes/blob/c53220435f8899e4fa39bab0a1b38e52695b5e72/lab/research/REPRODUCE.md) supplies the corresponding procedure against the notes' explicitly cited canonical revision, `ba3b94ba3a97c3262099da73a25a3a33f06c34ee`. These checks verify saved arithmetic; they do not refit the model, independently re-extract SEC filings or reconstruct historical publication availability.

## Data and source preservation

The review changed application behavior, validation, documentation and publication structure. It preserved the frozen numerical observations and original reported study results. Metadata definitions were corrected where needed; a metadata correction is not a new observation or experiment.

- **Storage:** the source CSVs, saved forecast state and replay CSV retained their hashes. The regression replay still has 463 evaluation weeks and reproduces the stored model MAE, baseline MAE and coverage. The displayed 20.50 Bcf versus 30.50 Bcf result remains retrospective. [Frozen-data record](https://github.com/NeuraX-JB/henry-hub-storage-forecaster/blob/4f884fe41be2f2a88a023f78a9a539110df8953d/SOURCE_SNAPSHOT.json)
- **Weather:** `runs.json` and `map.json` retained their hashes; the eight-cycle forecast archive was not rebuilt. [Frozen-data record](https://github.com/NeuraX-JB/natural-gas-weather-monitor/blob/23c19cce1a43177e18960ad71663bcea1f94e58e/SOURCE_SNAPSHOT.json)
- **Futures curve:** the bundled `market.js` data remained unchanged. [Frozen-data record](https://github.com/NeuraX-JB/henry-hub-futures-curve/blob/23afbe7e295a5b262f820e72491040153acc6f73/SOURCE_SNAPSHOT.json)
- **Industrial simulator:** the market asset and forward-audit CSV retained their hashes; the source-rebuild tests reproduce the existing 156 forward-price rows and their source URLs. [Frozen-data record](https://github.com/NeuraX-JB/industrial-gas-cost-simulator/blob/f16dd2fb61464c2e59528b764a542eb6d1473a56/SOURCE_SNAPSHOT.json)
- **Data API:** the three source CSVs were unchanged, and the temporary build reproduced the observation JSON byte-for-byte. Catalog wording and interface validation were corrected without changing observation values. [Frozen-data record](https://github.com/NeuraX-JB/natural-gas-data-api/blob/896d514361aea9f81400616d9b1d70be64322678/SOURCE_SNAPSHOT.json)
- **Research notes:** arithmetic checks preserve the reported results while the text clarifies evidence status and methodology. The notes' empirical revision is identified separately from the later packaging revision. Its snapshot manifest contains no bundled data hashes, so its relevant numerical evidence is the explicit arithmetic check above. [Edition record](https://github.com/NeuraX-JB/natural-gas-research-notes/blob/c53220435f8899e4fa39bab0a1b38e52695b5e72/SOURCE_SNAPSHOT.json)

Publication checks compared the Git blob hashes of changed files with the validated local copies and confirmed the resulting branch heads. Updates used an expected previous head and a non-forced ref update. The original canonical repository's `main` was read back at **`80c2e5321dadc95aadd4c7f65792fb15f0e2f156`**, unchanged by this review. [Canonical revision](https://github.com/NeuraX-JB/Henry-Hub-Futures-Curve-Explorer-How-the-Natural-Gas-Market-prices-winter/commit/80c2e5321dadc95aadd4c7f65792fb15f0e2f156)

## Browser verification

Live checks were performed on the deployed GitHub Pages editions in the cloud browser on **23 November 2026**. These were direct UI interactions and observations of rendered content, separate from the Node DOM substitutes described below.

| Project | Observed live behavior |
| :--- | :--- |
| Storage | Opened the landing and research tool; inspected the desktop dashboard and frozen-snapshot notice. Switching history from 26 to 13 weeks updated the chart, and the expanded table contained 13 data rows. The historical scorecard showed 463 weeks while completed registered scores remained zero. The final deployed revision displayed the corrected stock-change description, “Estimated stock decrease” label and Bcf on every numeric weekly-table header. |
| Weather | Opened the landing and comparison tool. Selected Pennsylvania and cooling degree days; reloading preserved both selections in the URL. Equal initialization times produced the invalid-pair message and hid results. “Latest archived pair” restored a valid comparison and enabled export. Inspected the desktop map and chart layout. |
| Futures curve | The deployed `?view=spread` link selected the EIA archive and March–April spread. Expanding the table from 12 to 62 rows moved focus to the first newly revealed row. ArrowRight on the chart produced a point announcement with calendar-day position, USD/MMBtu units and both series values. The final deployed hero was visually rechecked after the contrast correction; its historical-snapshot notice is readable against the dark background. |
| Industrial simulator | An entered 4.12 assumed quote survived a change of winter. An empty quote at 50% fixed produced a linked error and hid results; 0% fixed disabled the unused field and displayed identical budgets with a $0.00 effect. The result status announced the recalculation. Reset restored the default season and curve. Inspected the desktop form and budget layout. |
| Data API | Opened the landing, explorer and status page. Catalog-dependent controls started disabled and enabled after loading. “Latest week” rendered one record and correctly described an object response; the weather selection rendered a chronological array, preserving an observed zero. Captions and date row headers appeared in the accessibility tree. The status page visibly showed source dates, snapshot time, saved pipeline status and retrieval age. The desktop explorer and status layouts were visually inspected. |
| Research notes | Opened all four static reading pages: landing, storage article, curve article and reproduction guide. The storage article visibly placed its evidence qualifications before the main result. The accessibility tree exposed captioned storage and nine-contract comparison tables, section navigation, source links and reproduction commands. Inspected the storage article typography and desktop reading width. |

**Storage deployment follow-up:** an ordinary reload initially mixed the new HTML with an older cached script. The final HTML now requests the script using a content-derived version query. A new live reload of commit `4f884fe41be2f2a88a023f78a9a539110df8953d` displayed the corrected stock-change description and “Estimated stock decrease”; the expanded weekly table showed Actual, Model, Baseline and 80% range in Bcf.

These checks cover representative desktop flows. They are not a cross-browser, mobile-device or screen-reader certification. Responsive CSS and accessibility attributes were also inspected in source; those inspections are identified separately in the individual findings. Network-timeout and malformed-data edge cases were covered by code review or automated fixtures where stated, not by deliberately disrupting the public sites.

## What these checks establish, and their limits

**Code correctness has bounded evidence.** The test suites exercise the specified numerical rules, malformed-input guards, state transitions and selected failure paths. They cannot prove that every possible input or platform behaves correctly. The named successful Actions runs are tied to the six listed commits, rather than to an unspecified later version.

**DOM test doubles are not browser rendering.** Weather, curve and industrial controller tests run real application code against small DOM substitutes; storage presentation tests use a lightweight SVG/document stub. They can check generated content, events, selected focus behavior and boundary states. They do not implement CSS layout, a real accessibility tree, browser networking, download dialogs or native focus behavior. The API's Node cases validate data contracts rather than executing its complete page. Actual live-page observations belong in the browser section above and should not be inferred from these tests.

**The research editions remain historical snapshots.** Passing CI and deploying Pages do not make stored observations current, keep upstream services available or enable an automated research refresh. Archive dates and compilation timestamps remain part of the interpretation.

**Retrospective fit is separate from prospective skill.** The storage replay uses observed weather and current-vintage historical inputs. Its 463-week result and nominal interval coverage do not establish information availability at each original release. No completed live forecasts were scored in the frozen edition. The 2026 annual group is partial.

**The projects answer different questions.** GFS degree days describe temperature exposure, not a direct estimate of natural-gas demand. The curve note describes differences between saved prices, not causal drivers. Industrial scenarios depend on the supplied consumption, price and hedge assumptions; a successful arithmetic test does not validate those assumptions as a real procurement outcome. The saved-data API provides observation dates and source metadata, not a reconstructed point-in-time publication feed.

**Hashes establish preservation, not external truth.** Matching a frozen file proves that this review did not silently alter that artifact. It does not independently validate every upstream measurement, source extraction, economic interpretation or redistribution right. API staged publication also remains subject to the documented filesystem and two-rename deployment limits.

See the [complete findings](AUDIT_100.md), [machine-readable findings](audit-findings.json), and each project's `VALIDATION.md` and source notes for the exact changes and their evidence.

