# Portfolio review: 100 findings and fixes

**John Barreto · 23 November 2026**

This review covers the public profile and six project repositories. It records concrete defects and improvements in correctness, interpretation, reproducibility, navigation, accessibility and maintainability. The items do not have equal severity: an invalid-value bug matters more than a wording improvement.

The numerical research datasets and original reported study results are preserved. The original canonical research site and private repositories are outside this change set.

## Verification and publication

Project regression tests, local-link checks, strict JSON parsing and frozen-data hash checks accompany the fixes. Each repository documents its commands in `VALIDATION.md`; its source revision and reviewed baseline appear in `SOURCE_SNAPSHOT.json`. External-site availability, future forecast performance and universal browser compatibility are not claims of these offline checks.

See [publication and verification results](REVIEW_RESULTS.md) for final commits, deployed demos, test counts and material limitations.

## Findings

### Profile and portfolio engineering

#### 1. The introduction describes interests without telling a reader what they can inspect.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** Opening paragraph lists research subjects and activities.

**Fix:** Rewrite the introduction around inspectable evidence and replace the keyword-stuffed public bio with plain research language.

**Verification:** Editorial comparison with the baseline; new bio saved through GitHub profile controls.

**Repository files:** `README.md`

**Interface locations:** GitHub profile bio

#### 2. There is no recommended route into six unrelated-looking projects.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** The first navigation is a flat Selected projects table.

**Fix:** Add three concrete reader questions with direct study/tool entrypoints.

**Verification:** Check each route against the matching project.

**Repository files:** `README.md`

#### 3. Projects of different evidential maturity appear equivalent.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** Focus column does not classify archive, replay, scenario or dataset.

**Fix:** Add an Evidence type column distinguishing each project’s role.

**Verification:** Compare classifications with project source and limitations.

**Repository files:** `README.md`

#### 4. The main research result is buried beneath the complete project directory.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** Featured research follows six large project rows.

**Fix:** Place the worked result before the detailed directory.

**Verification:** Rendered profile reading-order review.

**Repository files:** `README.md`

#### 5. The headline performance figure has no evaluation dates on the profile.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** Profile says 463 weeks without start/end dates.

**Fix:** State 5 January 2018–13 November 2026 beside the comparison.

**Verification:** Dates match storage/state.json and the frozen replay.

**Repository files:** `README.md`

#### 6. Mean absolute error is not defined for a new reader.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** Profile gives MAE values but no plain-language interpretation.

**Fix:** Explain average absolute miss and that lower is better.

**Verification:** Definition agrees with the recorded research method.

**Repository files:** `README.md`

#### 7. The relative improvement lacks an absolute change alongside it.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** Only 32.8 percent relative improvement is emphasized.

**Fix:** Show the 10.00 Bcf absolute difference and both baseline/model values.

**Verification:** 30.503239740820735 − 20.50133495446041 rounds to 10.00 Bcf.

**Repository files:** `README.md`

#### 8. The profile leaves the absence of scored live forecasts implicit.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** Caveat says performance is not verified live, but omits the live-score count.

**Fix:** State zero completed scored live forecasts in the dated snapshot.

**Verification:** storage/state.json live_score.n equals 0.

**Repository files:** `README.md`

#### 9. Readers cannot directly inspect frozen evidence from the profile.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** The single research link points to a mutable main-branch note.

**Fix:** Link exact-commit results CSV, model source and model state, plus reproduction instructions.

**Verification:** Targets use published storage commit 30148e34…; source data verified.

**Repository files:** `README.md`

#### 10. The tool list does not explain the research process.

**Location:** [NeuraX-JB](https://github.com/NeuraX-JB/NeuraX-JB)

**Before:** Tools are presented as a list of technologies.

**Fix:** Explain the role of each tool and how observations, forecasts and decision cutoffs are distinguished.

**Verification:** Editorial review against actual repository methods.

**Repository files:** `README.md`

#### 11. There is no structured way to report a research or interface error.

**Location:** Across the portfolio

**Before:** Profile has no correction route; repositories have no issue template.

**Fix:** Add a correction section and form requesting location, inputs, observed/expected behavior and evidence.

**Verification:** Validate template YAML and inspect the published form.

**Repository files:** `README.md`, `.github/ISSUE_TEMPLATE/research-correction.yml`

#### 12. The new snapshots lack a machine-readable source revision record.

**Location:** Across the portfolio

**Before:** Root READMEs link the canonical repo, but there is no structured baseline manifest.

**Fix:** Record source revision, reviewed baseline and publication mode in SOURCE_SNAPSHOT.json.

**Verification:** Compare source/base commit identifiers with GitHub branches and original package metadata.

**Repository files:** `SOURCE_SNAPSHOT.json`

#### 13. Running verification requires finding scattered project-specific commands.

**Location:** Across the portfolio

**Before:** Tests exist in several subdirectories with no common launcher.

**Fix:** Provide python scripts/validate.py and documented setup.

**Verification:** Run the same command locally and in CI.

**Repository files:** `scripts/validate.py`, `scripts/checks.json`, `VALIDATION.md`

#### 14. Broken HTML and stylesheet references have no automatic detection.

**Location:** Across the portfolio

**Before:** No local web-link validation exists in the published repositories.

**Fix:** Check relative targets, project-root compatibility, directory entrypoints and cross-file HTML anchors.

**Verification:** Run against project HTML/CSS; missing targets, root-relative links and missing cross-file HTML anchors fail. Same-page fragment-only links are not checked.

**Repository files:** `scripts/validate.py`

#### 15. Broken Markdown documentation links have no automatic detection.

**Location:** Across the portfolio

**Before:** Copied DATA_SOURCES links target omitted folders in multiple repos.

**Fix:** Validate Markdown link targets after excluding fenced code examples.

**Verification:** Initial check catches absent copied attribution links; corrected repos pass.

**Repository files:** `scripts/validate.py`

#### 16. JSON artifacts can become invalid without a repository-wide check.

**Location:** Across the portfolio

**Before:** No shared strict parser validates JSON and notebooks on changes.

**Fix:** Reject invalid syntax, duplicate keys and non-standard numeric constants.

**Verification:** Parse all published JSON/notebooks with strict rules; regression fixtures exercise rejection.

**Repository files:** `scripts/validate.py`

#### 17. A code-cleanup commit can accidentally change the frozen research inputs.

**Location:** Across the portfolio

**Before:** Published split repos have no preservation check tied to their review baseline.

**Fix:** Hash frozen CSVs and selected observation/state JSON; fail when bytes change.

**Verification:** Hashes match pre-review packages; altered-fixture check fails.

**Repository files:** `SOURCE_SNAPSHOT.json`, `scripts/validate.py`

#### 18. The repositories lack automated verification on future pushes and pull requests.

**Location:** Across the portfolio

**Before:** No .github/workflows exists in the published snapshots.

**Fix:** Add a read-only verification workflow with pinned actions, explicit runtimes and validation dependencies.

**Verification:** Local regression suites and the published GitHub Actions run.

**Repository files:** `.github/workflows/verify.yml`, `scripts/requirements-ci.txt`

#### 19. Local runtime artifacts and environment files are not excluded from commits.

**Location:** Across the portfolio

**Before:** No .gitignore exists in the published split repos.

**Fix:** Ignore Python caches, virtual environments, node_modules and local .env files.

**Verification:** git check-ignore confirms representative generated/local paths are excluded.

**Repository files:** `.gitignore`

#### 20. The repositories’ demo links do not serve their own reviewed code.

**Location:** Across the portfolio

**Before:** All original Explore links point to the canonical research site; Pages is disabled for the inspected new repository.

**Fix:** Publish standalone project demos from the new repositories and direct profile links to them.

**Verification:** Verify deployed root/app pages and their current repository source.

**Repository files:** `README.md`, `.nojekyll`

**Interface locations:** GitHub Pages settings

### Storage forecaster

#### 21. The standalone project has no root web entry and its app home link leads to a placeholder.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** Baseline tree has no index.html; lab/storage/index.html links ../ to lab/index.html, whose only destination is the canonical lab.

**Fix:** Add an accessible project landing page, route app navigation home locally, and direct README visitors to the standalone demo.

**Verification:** Static link validator passes all local destinations; inspected heading, skip-link, responsive layout CSS and historical-status text. The deployed landing and storage tool were opened in the cloud browser.

**Repository files:** `index.html`, `lab/index.html`, `lab/storage/index.html`, `README.md`

#### 22. Storage attribution sends readers to source files absent from this extracted repository.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** DATA_SOURCES.md links lab/weather/README.md, lab/weather/research/US_ATLAS_LICENSE and lab/api/v1/index.json, none present in the baseline tree.

**Fix:** Replace copied cross-project attribution with the EIA/CPC sources and local shared-data provenance actually used by storage research.

**Verification:** All rewritten relative links pass scripts/validate.py --static-only.

**Repository files:** `DATA_SOURCES.md`

#### 23. The dashboard omits snapshot and target qualifications needed to interpret its estimate.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** lab/storage/index.html says Current forecast and describes gas entering or leaving storage; app.js never renders state.json as_of (2026-11-23T00:56:53Z) and labels stock changes as injections/withdrawals. Replay vintage limits are inside collapsed method notes, and the stock-change sign convention omits reclassifications.

**Fix:** Display the historical snapshot date above the app, identify the separately maintained canonical dashboard, and put retrospective/current-vintage limits directly next to replay scores. Describe the target as working-gas stock change, label increases/decreases accordingly, and explain that net stock changes can include reclassifications and need not equal physical flows. Version the JavaScript URL from its content hash so a previously cached script does not retain the superseded terminology.

**Verification:** Checked displayed timestamp against state.json; archived values and zero completed live scores remain unchanged; static data-hash validation passes. Live browser review prompted the stock/flow wording clarification and exposed an older cached app.js after an ordinary reload. The version query matches the first 12 SHA-256 characters of the corrected script; existing storage tests pass after both follow-ups. After the final deployment, a live reload displayed the corrected hero and Estimated stock decrease label.

**Repository files:** `lab/storage/index.html`, `lab/storage/app.js`, `lab/storage/storage.css`

#### 24. Missing storage values are formatted as zero.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** app.js format uses Number(value), so format(null) becomes 0; sign also applies numeric coercion. Invalid date values can throw during formatting.

**Fix:** Require finite numbers, display an em dash for missing/nonfinite values, and handle invalid dates explicitly.

**Verification:** Node regression covers null, undefined, NaN, Infinity, numeric strings, genuine zero and negative values.

**Repository files:** `lab/storage/app.js`, `lab/storage/app.test.cjs`

#### 25. An empty replay history crashes chart rendering instead of showing an empty state.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** chart([]) still computes label indices and reads rows[i].week; historyTable([]) produces an unexplained blank table.

**Fix:** Show explicit empty-chart, empty-table and no-evaluation messages before numeric/date rendering.

**Verification:** Node regression invokes chart([]) and validates an empty snapshot; no invalid observation access occurs.

**Repository files:** `lab/storage/app.js`, `lab/storage/app.test.cjs`

#### 26. A one-week replay is invisible and repeats the same date labels.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** chart() draws only polylines; a one-coordinate polyline has no segment. The fixed 3/6-label loop repeats that observation.

**Fix:** Center a single observation, draw three visible markers, and limit labels to available weeks.

**Verification:** Single-week chart regression asserts three circle markers and no NaN coordinates.

**Repository files:** `lab/storage/app.js`, `lab/storage/app.test.cjs`

#### 27. Overflowing storage tables are not reachable as scroll regions by keyboard.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** Both table-scroll containers lack tabindex/region labels; column headers lack scope and model/baseline columns omit units.

**Fix:** Add named, focusable table regions, visible focus styling, column scopes and Bcf labels, including every numeric weekly-values header (Actual, Model, Baseline and 80% range).

**Verification:** Inspected both HTML table wrappers and headers; static validation passes. No real-browser accessibility certification is claimed. The deployed 13-week history selection showed 13 accessible table rows. The final deployed weekly table also showed Bcf in Actual, Model, Baseline and 80% range headers.

**Repository files:** `lab/storage/index.html`, `lab/storage/storage.css`

#### 28. An open forecast page can keep its pre-release status after the scheduled release passes.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** forecast() and ledgerTable() evaluate Date.now only during initial render; no timer or visibility refresh updates those messages.

**Fix:** Extract a testable release-status function and refresh status/ledger each minute and when returning to the tab; clear repeated content first.

**Verification:** Boundary test verifies status before and exactly at scheduled release and rejects a forecast issued at the deadline.

**Repository files:** `lab/storage/app.js`, `lab/storage/app.test.cjs`

#### 29. Archive loading can hang indefinitely and a failed request gives no retry path.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** The baseline fetch(state.json) has no timeout or snapshot validation; its catch only provides a CSV link.

**Fix:** Add a 15-second abort, validate required snapshot observations, hide incomplete results, and expose a retry button alongside the CSV fallback.

**Verification:** Snapshot regression rejects bad dates, null replay observations and null forecast values; inspected abort/finally/retry handling; no network-dependent test.

**Repository files:** `lab/storage/app.js`, `lab/storage/storage.css`, `lab/storage/app.test.cjs`

#### 30. The model's chronology guard can miss a future training row before the last element.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** model.predict checks only train[-1][0].week >= row.week, so an out-of-order earlier array position can leak the target/future.

**Fix:** Require all selected training weeks to be distinct, sorted and strictly before the target.

**Verification:** Regression places the target at the first training position and confirms rejection; the 463-week replay still matches frozen metrics.

**Repository files:** `lab/storage/model.py`, `lab/storage/test_research_guards.py`

#### 31. Nonfinite training values and invalid calibration errors can contaminate model fitting or intervals.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** model.predict passes the feature matrix and response directly to lstsq and sorts previous_errors without checking finiteness or nonnegative absolute errors.

**Fix:** Validate selected features, responses, baseline and calibration errors before regression or interval computation.

**Verification:** Regression rejects infinite training outcomes, NaN errors and negative errors; unchanged historical replay passes.

**Repository files:** `lab/storage/model.py`, `lab/storage/test_research_guards.py`

#### 32. The model can run on CSVs that no longer match their recorded source manifest.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** refresh.load_shared reads storage.csv/weather.csv directly and never reads the manifest's existing SHA-256 fields.

**Fix:** Verify both CSV digests against lab/data/manifest.json before parsing or modeling.

**Verification:** A modified CSV with the old manifest is rejected before parsing; checked-in CSVs load and reproduce the recorded scores.

**Repository files:** `lab/storage/refresh.py`, `lab/storage/test_research_guards.py`

#### 33. Nonphysical CSV values are accepted as observations.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** refresh.load_shared converts stock, change, HDD and CDD with float() but does not reject NaN/Infinity, negative storage or negative degree days.

**Fix:** Reject nonfinite numbers, negative stock/degree-day values and empty source histories.

**Verification:** Matching-hash fixtures with NaN HDD, negative HDD and negative stock are rejected, separating content validation from the digest check.

**Repository files:** `lab/storage/refresh.py`, `lab/storage/test_research_guards.py`

#### 34. A malformed EIA bulletin can pass stock-change consistency checks.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** parse_report only checks abs(now-prev-change)>1; NaN makes that comparison false. Reporting-week and release-date order are not checked.

**Fix:** Require finite stock/change values, nonnegative stocks, a Friday reporting week and consistent publication/next-release dates.

**Verification:** Regression rejects NaN total stocks and a non-Friday week; a valid synthetic bulletin parses for captured-outcome reconciliation.

**Repository files:** `lab/storage/refresh.py`, `lab/storage/test_research_guards.py`

#### 35. Cached scoring records are trusted without reconciling their forecast week, raw release or publication window.

**Location:** [henry-hub-storage-forecaster](https://github.com/NeuraX-JB/henry-hub-storage-forecaster)

**Before:** refresh.run loads an existing release JSON and appends a scored row whenever a publication JSON exists; no read-time raw-hash/week/time reconciliation runs.

**Fix:** Reconcile captured outcomes with the raw EIA bytes and verify cached publication URL, commit format and pre-release timing before scoring.

**Verification:** Regressions cover altered raw hash, wrong forecast week, changed actual, valid captured release, wrong proof URL and publication at the release cutoff.

**Repository files:** `lab/storage/refresh.py`, `lab/storage/test_research_guards.py`

### Weather revision monitor

#### 36. The weather project has no standalone root web entry and navigation leaves visitors at a placeholder.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** Baseline has no root index.html; app brand/project links point ../ to a generic lab/index.html linking only the canonical site.

**Fix:** Add a historical-snapshot landing page, local project navigation and standalone README demo URL.

**Verification:** All local links pass static validation; inspected source dates, accessible skip navigation and responsive landing styles. The deployed landing and weather tool were opened and the desktop comparison layout was visually inspected.

**Repository files:** `index.html`, `lab/index.html`, `lab/weather/index.html`, `README.md`

#### 37. Weather attribution points to shared-data and API files absent from the repository.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** DATA_SOURCES.md includes lab/data/README.md, lab/data/manifest.json and lab/api/v1/index.json, absent from the weather package.

**Fix:** Document NOAA GFS, Census populations and us-atlas through the weather project's actual methodology, archive and license files.

**Verification:** Rewritten relative links pass scripts/validate.py --static-only; NOAA/Census metadata remains unchanged.

**Repository files:** `DATA_SOURCES.md`

#### 38. The comparison engine accepts archives whose declared units or method disagree with the UI.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** WeatherEngine.check validates schema/states/runs but ignores base_f, units, model, components, cycle, sample hours and weight. Reversed component order would silently exchange HDD and CDD.

**Fix:** Reject method metadata incompatible with the monitor's documented 65°F, four-sample, Census-weighted GFS calculation.

**Verification:** Regression rejects changed units/model/components and other method fields; the supplied archive still validates.

**Repository files:** `lab/weather/engine.js`, `lab/weather/research/weather.test.js`

#### 39. Weather date validation accepts impossible calendar dates.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** engine.check uses YYYY-MM-DD regexes only, which accept labels such as February 31.

**Fix:** Validate civil dates through an exact ISO round trip for initialization and valid-day labels.

**Verification:** Regression tests real leap dates and invalid dates, plus an archive with an impossible valid-day label.

**Repository files:** `lab/weather/engine.js`, `lab/weather/research/weather.test.js`

#### 40. Malformed or empty run/day structures can pass the archive check.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** check accepts an empty runs array and run.days={}, relies on states.length without an array check, and accepts arbitrary unique state codes rather than the covered geography.

**Fix:** Require nonempty run/day collections, complete numeric two-component state arrays and the exact Lower 48 plus DC state set with valid population weights.

**Verification:** Regression rejects empty/missing day structures, incomplete vectors and invalid state metadata; supplied 49-area archive remains valid.

**Repository files:** `lab/weather/engine.js`, `lab/weather/research/weather.test.js`

#### 41. The reusable engine computes equal or reversed forecast comparisons.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** WeatherEngine.calculate finds the two cycles without enforcing earlier<later; only the old page rendering later notices an invalid order.

**Fix:** Reject nonchronological input in the engine and prevent the page from calculating or exporting an invalid pair.

**Verification:** Engine tests reject equal/reversed cycles; page regression confirms invalid results are hidden and export is disabled. The deployed browser showed the invalid-pair message for equal initialization times, hid results, and recovered with Latest archived pair.

**Repository files:** `lab/weather/engine.js`, `lab/weather/app.js`, `lab/weather/research/weather.test.js`, `lab/weather/research/app.test.js`

#### 42. Selecting a state from the results table loses keyboard focus.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** The state-button handler calls setGeo(), which replaces the table containing that focused button, and only scrolls the heading without focusing anything.

**Fix:** Move focus to a programmatically focusable updated results heading and stop replay when geography is selected.

**Verification:** Page regression selects a table state and verifies focus moves to headline; heading has tabindex=-1 and focus styling.

**Repository files:** `lab/weather/app.js`, `lab/weather/index.html`, `lab/weather/style.css`, `lab/weather/research/app.test.js`

#### 43. A weather comparison cannot be preserved by refreshing or sharing its URL.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** Startup always selects the latest adjacent pair; the app neither reads nor writes selected vintages, measure or geography in the URL.

**Fix:** Persist choices as validated query parameters, restore valid comparisons and visibly explain unavailable saved selections.

**Verification:** Engine and page regressions restore a CDD/Pennsylvania comparison and test fallback for unavailable archive selections. In the deployed browser, a Pennsylvania/CDD comparison survived a page reload with the same URL parameters.

**Repository files:** `lab/weather/app.js`, `lab/weather/engine.js`, `lab/weather/index.html`, `lab/weather/README.md`, `lab/weather/research/weather.test.js`, `lab/weather/research/app.test.js`

#### 44. Different weather-measure exports have indistinguishable filenames.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** CSV filenames include geography and run dates but omit hdd/cdd/both, even though those exports contain different values.

**Fix:** Include the selected measure in the generated CSV filename and document it.

**Verification:** Filename regression verifies distinct HDD/CDD/BOTH names for the same geography and vintages.

**Repository files:** `lab/weather/app.js`, `lab/weather/engine.js`, `lab/weather/README.md`, `lab/weather/research/weather.test.js`

#### 45. Map colors change meaning between replay frames.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** drawMap derives its color limit from each selected comparison's maximum absolute state revision, so equal colors can encode very different degree-day changes across frames.

**Fix:** Use one symmetric scale per measure across all chronological comparisons in the loaded archive; label the fixed scale and retain a matched-window caveat.

**Verification:** Regression enumerates comparisons and verifies the selected fixed scale covers every state's cumulative revision.

**Repository files:** `lab/weather/app.js`, `lab/weather/engine.js`, `lab/weather/README.md`, `lab/weather/research/weather.test.js`

#### 46. Replay silently jumps from the newest archive back to the oldest.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** selectPair uses modulo indexing, so Next and timed playback wrap without announcing the chronological jump.

**Fix:** Bound pair navigation, disable endpoint buttons, stop at the newest pair and make restart an explicit labeled action.

**Verification:** Page regression advances replay to its endpoint, checks that it stops, verifies Next is disabled and tests the final-step boundary.

**Repository files:** `lab/weather/app.js`, `lab/weather/README.md`, `lab/weather/research/app.test.js`

#### 47. Controls look available while data is loading or after archive loading fails.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** index.html controls are enabled before event handlers/data exist; load has no timeout and catch does not disable controls or hide potentially partial results.

**Fix:** Start controls disabled, enable them only after successful validation, time out stalled loads and keep unavailable controls/results disabled or hidden on error.

**Verification:** Failed-fetch page regression verifies all nine controls stay disabled, content is hidden and the error is readable.

**Repository files:** `lab/weather/app.js`, `lab/weather/index.html`, `lab/weather/research/app.test.js`

#### 48. Users without JavaScript see a permanent loading message with no direct explanation or data fallback.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** Weather index.html contains no noscript element; initialization metadata and all comparisons require JavaScript.

**Fix:** Add a no-script explanation with direct archive and methodology links.

**Verification:** Inspected noscript markup and validated its local runs.json destination; existing numerical data remains untouched.

**Repository files:** `lab/weather/index.html`

#### 49. Merging newly built runs silently replaces an already archived cycle and incompletely checks method compatibility.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** build_runs.py uses built.update for matching initializations; its merge gate checks only schema, census hash, states, base and sample hours.

**Fix:** Require identical duplicate cycles by default, reject changed method/units/weights, and make deliberate replacement an explicit --merge --replace-existing choice.

**Verification:** Standard-library tests cover idempotent duplicate cycles, rejection/explicit replacement of changed cycles and incompatible method fields; no data was rebuilt.

**Repository files:** `lab/weather/research/build_runs.py`, `lab/weather/research/archive_rules.py`, `lab/weather/research/test_archive_rules.py`, `lab/weather/README.md`

#### 50. Cached temperatures bypass the physical bounds applied to freshly downloaded samples.

**Location:** [natural-gas-weather-monitor](https://github.com/NeuraX-JB/natural-gas-weather-monitor)

**Before:** Fresh sample() rejects temperatures below -100°F or above 150°F, while the cache branch checks only shape and finiteness.

**Fix:** Use one shared vector-shape, finite-value and physical-range validator for both fresh and cached temperatures.

**Verification:** Standard-library regression covers boundary values, NaN, out-of-range values, nested vectors, wrong shape and empty samples; no GDAL or network dependency.

**Repository files:** `lab/weather/research/build_runs.py`, `lab/weather/research/archive_rules.py`, `lab/weather/research/test_archive_rules.py`, `lab/weather/README.md`

### Futures curve explorer

#### 51. Attribution links refer to datasets absent from this standalone repository.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** DATA_SOURCES.md linked lab/data/README.md, lab/data/manifest.json, lab/weather/README.md, lab/weather/research/US_ATLAS_LICENSE and lab/api/v1/index.json; none were shipped in this project.

**Fix:** Replaced the copied portfolio-wide attribution with the two actual curve sources, exact frozen coverage, original EIA references and the local SEC source map.

**Verification:** python scripts/validate.py --static-only: all 24 local links pass; scoped source counts agree with market.js.

**Repository files:** `DATA_SOURCES.md`

#### 52. Project navigation and its downloaded guide direct readers to the old installation or nonexistent files.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** README and research example URLs opened the canonical site; lab/index.html linked only the canonical portfolio and a README. The embedded downloaded guide instructed users to open Open_Explorer.html, which was not included.

**Fix:** Pointed the primary demo and example to this project, made the research note and lab guide navigate locally, and replaced the stale embedded download with the maintained README.

**Verification:** Local-link validation passes; guide now downloads the actual README.md, with working root-server instructions.

**Repository files:** `README.md`, `lab/index.html`, `lab/research/curve-repricing.md`, `app.js`

#### 53. The standalone app does not clearly disclose its frozen-data status where users choose comparisons.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** The hero said Compare Henry Hub settlements without stating that this standalone edition has no live feed or refresh. Coverage dates appeared only in the footer, and the seasonal control called every date a Settlement date despite SEC reconstruction.

**Fix:** Added a prominent dataset-specific historical-snapshot label with its latest observation date, changed the generic wording to historical prices and Observation date, and documented the distinct archive cutoffs and delayed filing publication. A live screenshot exposed insufficient contrast in the added snapshot label; its inline foreground was changed from #315a55 to #d2e8df against the #102e30 hero, preserving layout.

**Verification:** Controller regressions initialize both source types; frozen-data tests verify 7,012 EIA dates and the unchanged SEC snapshot; static docs and dynamic banner use the stored data dates. The foreground/background contrast calculated from sRGB relative luminance is 11.23:1 (previously 1.87:1). The full local validator and all 12 curve regressions pass after this CSS-only correction. This color-pair calculation does not certify whole-page accessibility; the final live screenshot is reviewed separately. The final deployed page was reloaded and its corrected historical-snapshot notice was visually confirmed in a desktop screenshot.

**Repository files:** `index.html`, `app.js`, `README.md`

#### 54. A link specifying only the March–April view opens the wrong default dataset.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** restoreURL started with active=strips, read view=spread, then assigned preferredDataset[view]=active without consulting the spread default. Thus ?view=spread silently used quarterly strips instead of the intended daily archive.

**Fix:** Resolve the requested view first, then choose an explicit valid dataset or that view's declared default.

**Verification:** Node DOM regression checks ?view=spread → archive, explicit data=strips → strips, and invalid data with winter view → strips. The deployed ?view=spread URL selected the EIA daily archive and March–April view.

**Repository files:** `app.js`, `tests/ui.test.cjs`

#### 55. An older failed import can replace the success message from a newer import.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** The asynchronous CSV success path checked its request sequence after file.text(), but the catch path always replaced import feedback. A deferred rejection from an earlier file could overwrite a later successful import.

**Fix:** Guard import errors with the same request-sequence check used by successful reads.

**Verification:** Regression starts an old pending read, imports a newer valid file, rejects the old read, and verifies the success message and imported dataset remain intact.

**Repository files:** `app.js`, `tests/ui.test.cjs`

#### 56. Finite but extreme CSV prices can overflow spreads and chart arithmetic.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** validateRow accepted any Number.isFinite price; values such as +1e308 and -1e308 pass that check but produce infinite differences and sums.

**Fix:** Define and explain a supported ±1,000,000,000 USD/MMBtu numeric range, validating both parsed and directly indexed observations before calculation.

**Verification:** Tests reject ±1e308 through both CSV and index entry points, retain negative prices, and calculate a finite spread at the supported boundaries; all original snapshot prices remain accepted.

**Repository files:** `engine.js`, `README.md`, `tests/engine.test.cjs`

#### 57. Accepted four-digit years below 1000 break the seasonal view.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** winterView passed s.wy+"-11" to monthIndex. For an accepted 0001 CSV year, this becomes "1-11"; fixed-position slicing then produces NaN labels although the underlying date validator permits 0001.

**Fix:** Create seasonal delivery labels through a validated helper that pads the year to four digits and rolls November–October correctly.

**Verification:** An actual year-0001 import now renders all 12 seasonal rows, with winter 4.000, summer 3.000 and premium 1; invalid season bounds are rejected.

**Repository files:** `engine.js`, `app.js`, `tests/engine.test.cjs`, `tests/ui.test.cjs`

#### 58. Expanding table rows removes the keyboard-focused pagination button.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** table.append called more.remove() on every expansion and did not transfer focus; the final expansion permanently removed the active button.

**Fix:** Keep the pagination node while more rows exist and move focus to the first newly revealed row, including on the final page.

**Verification:** DOM regression expands every page and confirms focus lands on the first new row each time, including the last page. In the deployed browser, expanding 12 rows to 62 focused the first newly revealed row.

**Repository files:** `app.js`, `index.html`, `tests/ui.test.cjs`

#### 59. Resizing the chart discards keyboard focus and the selected observation.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** paint replaced the host SVG and reinitialized selected=-1; ResizeObserver redrew it without remembering whether the chart had focus.

**Fix:** Persist the selected index in chart state and restore SVG focus without scrolling after a resize; reset selection only for a new chart configuration.

**Verification:** Regression focuses the chart, advances a point, triggers ResizeObserver, and verifies both the focused SVG and spoken selected point survive.

**Repository files:** `plot.js`, `tests/ui.test.cjs`

#### 60. Point-by-point chart announcements rely on axis context announced when entering the chart.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** The original SVG accessible label already included the x-axis context and y-axis units. Subsequent live-region messages from inspect included the point label, series name and numeric price without repeating that context.

**Fix:** Repeat the x-axis meaning and y-axis units in each concise point-by-point live announcement. This is a usability improvement; the original chart already provided axis context.

**Verification:** Keyboard chart regression verifies the announcement includes Delivery month and USD / MMBtu; the same code uses calendar-day context in spread view. In the deployed spread chart, an ArrowRight interaction announced the calendar-day position, USD/MMBtu units and both series values.

**Repository files:** `plot.js`, `tests/ui.test.cjs`

#### 61. Curve data tables have no caption or semantic row headers.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** table created only column headers and rendered every body cell as td. The section heading did not give the table its own caption or associate each numeric row with its delivery identifier.

**Fix:** Add a table caption naming the comparison and USD/MMBtu units, and render the first cell of every body row as a scoped row header.

**Verification:** DOM table regression confirms a units caption and scope=row headers, including dynamically appended rows; local checks pass.

**Repository files:** `app.js`, `index.html`, `tests/ui.test.cjs`

#### 62. The explorer starts with an enabled export and offers no JavaScript-disabled fallback.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** The initial HTML enabled Export CSV while results were empty, omitted noscript guidance, and its initialization error referred to a standalone project download that was not provided in this repo.

**Fix:** Disable export until results exist, show an initial loading status, provide direct project/research links without JavaScript, and make failures link to the actual setup guide.

**Verification:** Static inspection confirms noscript links and disabled initial export; successful controller tests enable export only after table results are populated; link validation passes.

**Repository files:** `index.html`, `app.js`

#### 63. Downloaded comparisons lose the provenance that explains their prices.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** CSV columns held comparison dates and numeric results only; the selected SEC filing URLs, EIA source, reconstruction distinction and frozen source commit were absent.

**Fix:** Append dataset, price origin, applicable original source URLs and the source snapshot commit to every exported row. Imported filenames are prefixed as descriptive text rather than emitted as a formula-like cell.

**Verification:** CSV regression downloads the June–September SEC comparison and verifies both filing URLs, the four provenance columns and commit 80c2e5321dadc95aadd4c7f65792fb15f0e2f156.

**Repository files:** `app.js`, `README.md`, `tests/ui.test.cjs`

#### 64. The Latest week preset claims a calendar period it does not implement.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** The preset used dates.at(-6) through dates.at(-1). The actual final selected dates run 2024-03-28–2024-04-05, an eight-day span in a historical archive, not the latest calendar week.

**Fix:** Rename the preset Last 6 archived observations to state the selection rule and historical context directly.

**Verification:** Checked the six stored dates: 2024-03-28 and 2024-04-01 through 2024-04-05; the comparison endpoints remain unchanged.

**Repository files:** `app.js`

#### 65. Unavailable observation dates are not programmatically linked to their error.

**Location:** [henry-hub-futures-curve](https://github.com/NeuraX-JB/henry-hub-futures-curve)

**Before:** selectionOK displayed nearest-date suggestions in input-hint but did not mark the affected date control invalid or link it to that explanation.

**Fix:** Set aria-invalid on the affected control, associate the hint through aria-describedby, and clear invalid state when corrected.

**Verification:** Regression selects unavailable 2024-04-06, verifies the linked error, then corrects to 2024-04-05 and checks the invalid state clears.

**Repository files:** `app.js`, `tests/ui.test.cjs`

### Industrial cost simulator

#### 66. The standalone site has no root entry page and its navigation leads to a generic stub.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** The shipped files had no root index.html. The simulator header/footer pointed to lab/index.html, which only sent readers to the separate canonical portfolio and a README.

**Fix:** Create a responsive root landing page with a direct local simulator link, model assumptions and source audit; make the app and lab guide navigate within this project.

**Verification:** Static validation passes all 38 local links, including the root app entry, method anchor and audit download.

**Repository files:** `index.html`, `lab/index.html`, `lab/industrial/index.html`, `lab/industrial/style.css`, `README.md`

#### 67. The simulator's source document links to nonexistent and irrelevant portfolio files.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** DATA_SOURCES.md listed NOAA, Census and us-atlas plus missing lab/data, lab/weather and lab/api paths, while omitting a useful local explanation of its own market asset and forward audit.

**Fix:** Scope the document to EIA monthly cash, SEC fund positions and illustrative/user inputs; link the actual market, reconstruction and audit files.

**Verification:** Local-link validation passes; source counts match 358 cash months, 13 curves and the 156-row forward audit.

**Repository files:** `DATA_SOURCES.md`

#### 68. The simulator's frozen data can be mistaken for a maintained current price feed.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** The opening section identified industrial procurement but did not say the standalone edition was frozen. Release and coverage information appeared only at the bottom, and the README primary link opened the canonical application.

**Fix:** Display historical snapshot status at entry and above controls, derive cash coverage/release from the bundled asset, and document this project's no-refresh status and separate original site.

**Verification:** Initialized controller uses the stored October 2026 coverage and 18 November 2026 release; snapshot checksum test confirms the market asset is unchanged.

**Repository files:** `index.html`, `lab/industrial/index.html`, `lab/industrial/app.js`, `README.md`

#### 69. Sparse five-element arrays pass the model's validation and return false zero budgets.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** Array.every skips holes. On the published model, quantities=new Array(5) returned five sparse rows and quantity, variable, mixed, difference and local all equal to zero.

**Fix:** Validate a dense Array.from copy so missing positions are seen as invalid values for quantities, spot prices and forwards.

**Verification:** Regression rejects wholly sparse and partially sparse arrays in all three monthly inputs; ordinary five-month fixtures still pass.

**Repository files:** `lab/industrial/model.js`, `lab/industrial/model.test.cjs`

#### 70. The public calculation model returns Infinity or unusable chart ranges for finite inputs.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** The model checked input finiteness only. The original model returned mixed=Infinity for five finite 1e308 quantities; its aggregate UI guard did not validate every returned component or a positive-to-negative shared chart range.

**Fix:** Validate every computed row component, all returned totals and the shared monthly cost range before returning results.

**Verification:** Tests cover row multiplication overflow, total overflow and an infinite cross-zero chart range; all reject with an actionable calculation-range error.

**Repository files:** `lab/industrial/model.js`, `lab/industrial/model.test.cjs`

#### 71. Subtracting large total costs can erase a real fixed-price effect.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** The model used difference=mixed-variable after adding common local costs. With five units, cash 2, fixed 3, share 0.5 and basis 1e18, the published code returned difference=0 instead of 2.5.

**Fix:** Compute the effect directly as fixedVolume × (fixedPrice − spotPrice), avoiding cancellation of shared charges; document display precision and this calculation.

**Verification:** Regression reproduces large equal displayed totals while retaining the correct 0.5 monthly and 2.5 seasonal effect; existing normal-budget arithmetic remains correct.

**Repository files:** `lab/industrial/model.js`, `lab/industrial/model.test.cjs`, `lab/industrial/index.html`, `README.md`

#### 72. The model concatenates numeric-string winter years into invalid next-year labels.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** months("2025") returned 2025-11,2025-12,20251-01,20251-02,20251-03 because year+1 concatenated a string. Early years were not padded and out-of-range years were not rejected.

**Fix:** Normalize and validate an integer year from 1 through 9998, pad four-digit ISO labels, and exclude impossible start years when finding available winters.

**Verification:** Tests cover numeric strings, year 0001, invalid fractions/empty values, and both boundaries; all original complete winter seasons remain available.

**Repository files:** `lab/industrial/model.js`, `lab/industrial/model.test.cjs`

#### 73. Changing the winter silently replaces a manually chosen fixed quote.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** configureSeason always assigned curves[0] || manual after rebuilding options, so a user's manual scenario switched to an archived curve whenever the new winter had one.

**Fix:** Keep a manual selection and preserve an archived date when still eligible; only the explicit Reset action restores the default newest curve.

**Verification:** DOM regression keeps a 4.25 manual quote across a winter change, then verifies Reset restores the 2025-09-30 default curve. The deployed browser preserved an entered 4.12 quote across a change from winter 2025–2026 to 2024–2025, and Reset restored the default scenario.

**Repository files:** `lab/industrial/app.js`, `lab/industrial/ui.test.cjs`

#### 74. A 0% fixed scenario is blocked by a price that is not used in its calculation.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** assumptions validated the manual fixed-price field before reading share; a blank manual quote hid results even when fixed share was zero.

**Fix:** Read the share first, skip and disable an unused manual price at zero fixed volume, show Not applied in the fixed-price column and label the CSV accordingly.

**Verification:** Regression blanks the manual quote, switches to 0%, and verifies equal budgets, enabled output and an export explicitly marked Not applied (0% fixed). The deployed browser accepted an empty manual quote at 0% fixed, disabled the unused field, and displayed identical budgets with a $0.00 effect.

**Repository files:** `lab/industrial/app.js`, `lab/industrial/ui.test.cjs`, `README.md`

#### 75. Whole-dollar display contradicts sub-dollar savings or cost classifications.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** The currency formatter used maximumFractionDigits:0 while deltaSub classified differences as small as 0.005. A 0.20 effect could therefore display $0 and Higher seasonal cost.

**Fix:** Display monetary results to cents, label nonzero sub-cent differences explicitly, and align the positive-cost styling threshold with cent rounding.

**Verification:** Regression verifies a 0.20 effect displays $0.20 with Higher seasonal cost and a 0.001 effect is labelled Difference below $0.01.

**Repository files:** `lab/industrial/app.js`, `lab/industrial/index.html`, `lab/industrial/ui.test.cjs`

#### 76. Invalid assumption fields are not associated with the error shown below the form.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** inputValue only threw a global message; no input received aria-invalid or aria-describedby, so assistive technology could not identify the affected field from the input.

**Fix:** Mark the failing input invalid and associate the error, preserving any existing price explanation; clear only the error association once corrected.

**Verification:** Regression verifies invalid consumption is linked to the error, correction restores output, and the manual price retains its price-note description through invalid and valid states. The deployed browser exposed the missing-quote alert and the input description pointed to both price-note and error; switching to 0% fixed recovered valid output.

**Repository files:** `lab/industrial/app.js`, `lab/industrial/ui.test.cjs`, `lab/industrial/style.css`

#### 77. Recalculated results are explicitly silent to screen readers.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** The output container had aria-live=off and there was no separate live result summary, despite recomputing on every input event.

**Fix:** Add a concise polite atomic status message with the two budgets and effect, debounced until edits settle; clear it on invalid input.

**Verification:** Regression changes the share repeatedly, confirms only the latest announcement remains scheduled, and verifies the concise budget message after it runs. The deployed browser exposed the updated equal-budget status after the 0% scenario settled.

**Repository files:** `lab/industrial/index.html`, `lab/industrial/app.js`, `lab/industrial/ui.test.cjs`

#### 78. Monthly consumption controls omit units from their accessible names.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** Dynamic quantity labels contained only month text. MMBtu appeared in a separate section heading, leaving a focused quantity input without a unit in its name; output row identifiers were plain data cells.

**Fix:** Label each monthly input with month, consumption and MMBtu; reinforce the same unit relationships with a descriptive table caption and scoped month row headers.

**Verification:** DOM regression checks Jan 26 consumption in MMBtu and scoped row identifiers; the table caption defines volume, price and budget units.

**Repository files:** `lab/industrial/app.js`, `lab/industrial/index.html`, `lab/industrial/style.css`, `lab/industrial/ui.test.cjs`

#### 79. Failed or disabled JavaScript leaves empty controls and apparently available output.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** The original HTML showed dashed results and enabled Download CSV before initialization, had no noscript guidance, and app initialization outside a catch failed silently if its market asset was missing.

**Fix:** Hide output and disable download until calculation succeeds, provide a loading status and JavaScript-disabled guide, and catch initialization failures with a direct setup link.

**Verification:** Regression omits the market asset and verifies an actionable load error, hidden output and disabled export; static fallback links pass validation.

**Repository files:** `lab/industrial/index.html`, `lab/industrial/app.js`, `lab/industrial/ui.test.cjs`

#### 80. Forward-audit reconstruction silently overwrites duplicate observations and can misattribute a curve.

**Location:** [industrial-gas-cost-simulator](https://github.com/NeuraX-JB/industrial-gas-cost-simulator)

**Before:** get_curves assigned rec[prices][delivery_month] without checking whether that date/month was already read, and retained the first source URL even if later rows for the same date cited another filing.

**Fix:** Reject duplicate date/month keys and conflicting source URLs before building the market asset; accept an optional local audit path for deterministic fixture tests.

**Verification:** Three Python tests reject duplicates, reject conflicting sources, and rebuild all 156 original forward prices and source URLs exactly equal to the frozen market asset; no data were refreshed.

**Repository files:** `lab/industrial/refresh.py`, `lab/industrial/test_refresh.py`, `README.md`

### Natural gas data API

#### 81. The standalone project has no root page and its lab navigation sends visitors to the original portfolio.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** No index.html existed at repository root; lab/index.html offered only an external canonical-portfolio link, while README's primary demo URL also pointed there.

**Fix:** Added a local project landing with explorer, status, notebook and direct JSON entry points; pointed the primary demo and internal navigation at this standalone repository.

**Verification:** Shared static validator passes. The deployed project landing, explorer and status page were opened in the cloud browser; local navigation and populated responses were observed.

**Repository files:** `index.html`, `README.md`, `lab/index.html`, `lab/README.md`, `lab/api/index.html`, `lab/api/status.html`

#### 82. Data attribution names absent projects and contains broken license/methodology links.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** DATA_SOURCES.md linked lab/weather/README.md and lab/weather/research/US_ATLAS_LICENSE, neither of which is present, and listed SEC/GFS/geographic assets that the API does not bundle.

**Fix:** Replaced the copied portfolio-wide table with attribution for the actual EIA/NOAA observation series, existing local manifest/catalog links, and the spot provider's reuse qualification.

**Verification:** Shared validator passes all local links; attribution scope reconciled with the three source CSVs and manifest.

**Repository files:** `DATA_SOURCES.md`

#### 83. CSV parsing silently accepts duplicate headers and malformed row widths.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** read_csv only checked that required headers were a subset; DictReader can overwrite a duplicate column and put surplus cells under None, while missing optional cells became null.

**Fix:** Require exactly the unique expected headers and reject both missing and surplus cells before type conversion.

**Verification:** New regression test rejects duplicate change_bcf headers, a truncated row, and an extra cell. The complete Python suite passes (12 tests).

**Repository files:** `lab/api/build_api.py`, `lab/api/test_api.py`

#### 84. The API builder accepts impossible inventory levels and storage changes that contradict the supplied stocks.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** read_csv checked weather ranges but never checked working_gas_bcf or reconciled change_bcf with the prior Friday.

**Fix:** Reject negative inventories, reconcile changes for consecutive Fridays, and require null when the preceding Friday is absent; preserve a measured zero.

**Verification:** Regression cases reject negative inventory, a reversed-sign change and a change across a gap; valid zero and null cases pass. All frozen observation JSON reproduces byte-for-byte in a temporary build.

**Repository files:** `lab/api/build_api.py`, `lab/api/test_api.py`

#### 85. Loose date and timestamp handling can turn malformed provenance into apparently valid published metadata.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** date.fromisoformat accepted noncanonical ISO forms and normalized them; downloaded_at_utc was accepted whenever nonempty, and generated_at_utc was not parsed.

**Fix:** Require YYYY-MM-DD dates and full UTC timestamps; reject impossible calendar values and source retrieval timestamps later than their manifest generation time.

**Verification:** Tests reject compact/week dates, whitespace dates, impossible dates, offset/naive timestamps and arbitrary text; leap-day input passes. Catalog browser validation rejects invalid clocks.

**Repository files:** `lab/api/build_api.py`, `lab/api/test_api.py`, `lab/api/response.js`

#### 86. A failed or shortened rebuild can publish a mixed snapshot and leave obsolete annual endpoints.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** The original build wrote directly into the target one file at a time and never removed years absent from the new catalog. Root review also identified that unrestricted complete-directory replacement would endanger an unrelated existing --target.

**Fix:** Stage the whole managed directory, serialize builder runs with a lock, promote only a complete snapshot, restore the previous target on promotion failure, and remove obsolete partitions. Before staging and immediately before replacement, require an existing target to have a recognizable v1 API catalog and only valid managed endpoint/year files; reject unrelated files, catalogs, directories and symlinks. Document the two-rename deployment limit.

**Verification:** Regression cases preserve a sibling application, extra user notes, an unrelated v1 catalog and a non-API year JSON byte-for-byte, with no leftover staging/lock directories. Valid obsolete-year cleanup still passes. Simulated second-write and promotion failures retain the old edition; a concurrent lock prevents mutation. All 12 API Python tests pass.

**Repository files:** `lab/api/build_api.py`, `lab/api/test_api.py`, `lab/api/README.md`, `README.md`

#### 87. The preview and CSV export trust JSON arrays without checking their row schema, null semantics or endpoint shape.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** loadSelection validated only a non-array object's key, then passed every array through; malformed numbers could reach toFixed and missing fields could be exported as empty values. A one-row array was also described as a latest object.

**Fix:** Added a shared browser contract that validates catalog/row shapes, dates, numeric values, nulls, price counts and stock differences before enabling export; derive singleton wording from the selected endpoint.

**Verification:** Four Node tests pass: all published endpoints conform; malformed rows and incorrect array/object shapes fail; valid null and zero values remain distinct.

**Repository files:** `lab/api/response.js`, `lab/api/api.js`, `lab/api/test_response.cjs`, `lab/api/index.html`, `lab/api/status.html`

#### 88. The spot mean definition incorrectly treats observation dates as publication dates.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** FIELD_NOTES and v1/index.json said quotes were 'published within the seven-day window', although join_weekly selects spot rows by their observation date.

**Fix:** Corrected the builder and catalog definition to observation-date inclusion and explicitly stated that these dates are not publication timestamps.

**Verification:** Existing boundary-date join test passes; metadata-only diff reviewed. No observation JSON or CSV values changed.

**Repository files:** `lab/api/build_api.py`, `lab/api/v1/index.json`, `DATA_SOURCES.md`, `lab/api/README.md`

#### 89. The status interface can imply freshness without explaining its frozen edition or showing saved retrieval status, and hides the snapshot stamp on mobile.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** Source cards omitted the manifest's status and elapsed retrieval age; the legacy built_at_utc key was not explained; the responsive .heroaside rule hid the status timestamp.

**Fix:** Show a frozen-edition notice, saved pipeline status and elapsed retrieval age with clock/provider-availability qualifications; document the legacy timestamp's source-manifest meaning and retain the stamp at narrow widths.

**Verification:** Node tests check elapsed age and future-clock handling. HTML/CSS preserves the status stamp at narrow widths. The deployed desktop status page was visually inspected and showed the frozen-edition stamp, saved pipeline status, source coverage and retrieval age. Narrow-screen behavior was reviewed in CSS, not certified across devices.

**Repository files:** `lab/api/api.js`, `lab/api/response.js`, `lab/api/status.html`, `lab/api/index.html`, `lab/api/style.css`, `lab/api/README.md`

#### 90. Catalog failure leaves active controls and indefinite loading messages, and requests have no timeout.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** Dataset/copy controls started enabled before handlers/catalog were ready; main().catch only displayed an error; fetch could remain pending indefinitely.

**Fix:** Disable catalog-dependent controls until validation completes, add 25-second request deadlines, clear loading/busy states on failure, retain direct JSON links, and provide a no-JavaScript fallback.

**Verification:** JavaScript syntax and contract tests pass; error paths were inspected for disabled controls and resolved loading/busy states. In the deployed browser, controls were disabled during initial loading and enabled after the valid catalog loaded. Live network failures were not deliberately injected.

**Repository files:** `lab/api/api.js`, `lab/api/index.html`, `lab/api/status.html`, `lab/api/style.css`

#### 91. The notebook and stock-change descriptions equate reported inventory differences with physical injections and withdrawals.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** Notebook cell 4 stated 'A positive net storage change is an injection. A negative change is a withdrawal'; the catalog similarly used injection/withdrawal labels despite possible reclassifications.

**Fix:** Use stock increase/decrease terminology and explain the physical-flow distinction; point the notebook at this edition, print its snapshot timestamp, and clear old saved output that could otherwise appear to represent the selected mirror.

**Verification:** Notebook remains valid JSON with cleared execution counts/outputs; notebook code cells compile; observation inputs unchanged and the API regression suites pass.

**Repository files:** `lab/api/natural_gas_api.ipynb`, `lab/api/build_api.py`, `lab/api/v1/index.json`, `lab/api/README.md`

#### 92. The response table lacks a caption and row headers, and its missing-value dash is unexplained to assistive technology.

**Location:** [natural-gas-data-api](https://github.com/NeuraX-JB/natural-gas-data-api)

**Before:** The original table had only column headers, td cells for dates, no caption and a bare em dash for null values; focus styling excluded the scrollable table and code area.

**Fix:** Add a dynamic caption, scoped date row headers, explicit unavailable labels and a visible null/zero/CSV explanation; provide consistent focus outlines and a status-page skip link.

**Verification:** Static markup and DOM construction were inspected for caption, scope, unavailable labels and focus/skip affordances. The deployed browser exposed captioned tables and date row headers; Latest week rendered one JSON object and weather rendered an array with an observed zero preserved. This is representative browser inspection, not a screen-reader certification.

**Repository files:** `lab/api/api.js`, `lab/api/index.html`, `lab/api/status.html`, `lab/api/style.css`

### Research notes

#### 93. The extracted notes have no local reading interface and their primary link sends readers to a different website.

**Location:** [natural-gas-research-notes](https://github.com/NeuraX-JB/natural-gas-research-notes)

**Before:** No root index.html or publication HTML existed. README linked the canonical research directory; lab/index.html only redirected attention to that external portfolio.

**Fix:** Added a publication landing and complete static storage, curve and reproduction reading pages, with accessible table regions, section navigation, source links and responsive styles. Markdown remains the source via a deterministic stdlib renderer.

**Verification:** render_notes.py --check confirms all four pages are current; shared validator passes HTML/local links. The deployed landing, storage article, curve article and reproduction guide were opened in the cloud browser. The storage reading layout was visually inspected, and both evidence tables and section navigation appeared in the accessibility tree. Pages contain no runtime JavaScript.

**Repository files:** `index.html`, `lab/research/storage-weather.html`, `lab/research/curve-repricing.html`, `lab/research/reproduce.html`, `lab/research/render_notes.py`, `lab/assets/research.css`, `README.md`, `lab/README.md`, `lab/index.html`

#### 94. The notes' source policy points to nonexistent local manifests, APIs, weather methods and licenses.

**Location:** [natural-gas-research-notes](https://github.com/NeuraX-JB/natural-gas-research-notes)

**Before:** DATA_SOURCES.md linked lab/data/manifest.json, lab/api/v1/index.json and lab/weather paths that are absent from the eight-file notes package.

**Fix:** Replaced copied attribution with note-specific EIA/NOAA/SEC provenance, working local definitions, and exact frozen canonical evidence links; clarified which broader portfolio assets are outside this package.

**Verification:** All local links pass the shared validator; frozen links use the existing evidence revision cited by the original notes.

**Repository files:** `DATA_SOURCES.md`

#### 95. The source documentation instructs readers to run pipelines and tests that this repository does not contain.

**Location:** [natural-gas-research-notes](https://github.com/NeuraX-JB/natural-gas-research-notes)

**Before:** lab/data/README.md opened with python data/refresh.py and unittest commands and referred to three local CSVs and a manifest, although none is bundled here.

**Fix:** Explain the notes package's actual contents, link the frozen canonical data/manifest/model, route readers to the evidence guide, and narrow the unsupported claim that all upstream schema or network errors are caught.

**Verification:** Every new local target exists; documentation distinguishes reference methods from executable local instructions.

**Repository files:** `lab/data/README.md`, `lab/README.md`

#### 96. The quoted findings have no direct, frozen, read-only reproduction procedure in the standalone repository.

**Location:** [natural-gas-research-notes](https://github.com/NeuraX-JB/natural-gas-research-notes)

**Before:** The storage note's rebuild link led to generic lab navigation and complete-lab instructions, not a procedure to verify the 463-week table or fixed-contract arithmetic without refreshing data.

**Fix:** Added a pinned-checkout guide and a stdlib evidence checker for all annual/pooled replay statistics and nine curve pairs. It only reads supplied evidence and explicitly distinguishes arithmetic checks from model refits or prospective validation.

**Verification:** All 10 storage table rows match the unchanged replay CSV exactly at published precision; all nine curve price pairs/differences match the frozen original package. No data refresh or model fitting performed.

**Repository files:** `lab/research/REPRODUCE.md`, `lab/research/check_evidence.py`, `lab/research/storage-weather.md`, `README.md`

#### 97. Headline results and the README chart can be read before the essential retrospective qualification.

**Location:** [natural-gas-research-notes](https://github.com/NeuraX-JB/natural-gas-research-notes)

**Before:** The storage note led with 32.8% improvement and the chart/table; its nowcast/current-vintage/no-live-score qualification appeared later. README displayed the results image without that nearby qualification.

**Fix:** Put evidence status before the result, add the observed-weather/current-vintage/no-completed-live-score qualification beside the README and landing summary, preserve the partial-2026 limitation, and use descriptive chart alternative text.

**Verification:** Reviewed first-screen text ordering; all original reported result values remain unchanged and the evidence arithmetic check passes.

**Repository files:** `README.md`, `lab/research/storage-weather.md`, `lab/research/render_notes.py`, `index.html`, `lab/research/storage-weather.html`

#### 98. Interval coverage is reported without stating its nominal target or how the interval radius is selected.

**Location:** [natural-gas-research-notes](https://github.com/NeuraX-JB/natural-gas-research-notes)

**Before:** The storage table said only 'Interval coverage'; the method listed 52–104 calibration errors without giving the 80% target or rank rule implemented in model.py.

**Fix:** Label nominal 80% coverage, document the exact finite-sample rank and inclusive bounds, state the 1.8 percentage-point gap, and distinguish coverage from confidence in the MAE reduction or a guaranteed future rate.

**Verification:** Rank rule checked against the model's ceil(0.8*(n+1)) selection; the unchanged replay verifies 78.2% inclusive aggregate coverage.

**Repository files:** `lab/research/storage-weather.md`, `lab/research/storage-weather.html`

#### 99. The curve note asserts unequal repricing across overlapping months but shows only one contract and no direct filing pointers.

**Location:** [natural-gas-research-notes](https://github.com/NeuraX-JB/natural-gas-research-notes)

**Before:** The original note gave only January 2027's 4.391-to-3.752 example, then asserted the other overlapping months did not all change equally; evidence linked a large application file.

**Fix:** Expose all nine matched delivery months, both stored prices, September-minus-June differences and the app's exact SEC filing pointers; clarify exclusion of unmatched contracts and snapshot dates versus publication timing.

**Verification:** Decimal arithmetic check confirms all nine pairs and differences against the unmodified original source package; table explicitly says it reproduces stored app values rather than independently re-extracting filings.

**Repository files:** `lab/research/curve-repricing.md`, `lab/research/curve-repricing.html`, `lab/research/check_evidence.py`

#### 100. Individual notes lack author-specific citations and do not separate empirical evidence revision from later packaging/editorial changes.

**Location:** [natural-gas-research-notes](https://github.com/NeuraX-JB/natural-gas-research-notes)

**Before:** Each byline said only Henry Hub Research plus note number/date; individual source links pinned ba3b94ba while the extracted repository originated from a later source snapshot, without explaining the distinction.

**Fix:** Name John Barreto in both bylines, add reproducible citation/edition statements, identify the empirical revision separately from the standalone snapshot record, and state that editorial clarifications do not create new results.

**Verification:** Both Markdown and generated HTML carry matching author, date and empirical revision; renderer sync and local-link validation pass.

**Repository files:** `lab/research/storage-weather.md`, `lab/research/curve-repricing.md`, `lab/research/REPRODUCE.md`, `README.md`, `lab/research/storage-weather.html`, `lab/research/curve-repricing.html`

## Interpretation of the results

These fixes improve the reliability and inspectability of the software and its claims. They do not turn retrospective nowcasts into a point-in-time forecast evaluation, establish tradable profitability, fill historical data gaps, or create a new live performance record. The portfolio states those limits directly.
