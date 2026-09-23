[README.md](https://github.com/user-attachments/files/31944457/README.md)
# Web-Based Corpus Analyzer (WBCA) — Version 2

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Made with HTML/CSS/JS](https://img.shields.io/badge/Made%20with-HTML%2FCSS%2FJS-orange)](https://developer.mozilla.org/en-US/docs/Web)
[![Runs in browser](https://img.shields.io/badge/Runs-100%25%20in%20browser-brightgreen)](#-privacy--security)

**From word keyness to phraseological keyness.**

WBCA Version 2 is a free, open-source, browser-based corpus linguistics tool. It extends the KWIC-centred workflow of Version 1 from single words to **lemmas, n-grams, p-frames, and POS-grams**, so that word-level and phrase-level keyness can be computed and compared under one consistent statistical setting. The whole tool is a **single HTML file**: there is nothing to install, no server, and no account. **All processing happens locally in your browser — no data is ever sent anywhere.**

---

## 🌐 Access the Tool

| | Link |
|---|---|
| **Version 2 — Google Site (documentation + embedded tool)** | <https://sites.google.com/view/web-basedcorpusanalyzerver2/> |
| **Version 2 — run directly (GitHub Pages)** | <https://ishitatu.github.io/Web-based-corpus-analyzer-VER2/WBCA_1-8_ver2_20260908.html](https://github.com/ishitatu/Web-based-corpus-analyzer-VER2/blob/main/WBCA_1-8_ver2_20260924.html)> |
| **Version 2 — this repository** | <https://github.com/ishitatu/Web-based-corpus-analyzer-VER2> |
| **Version 1** | <https://github.com/ishitatu/Web-based-corpus-analyzer-> |
| **Companion Google Colab notebook (POS tagging / lemmatisation)** | <https://colab.research.google.com/drive/1W62nqzdKbIIPpUYXsvE2ReLU3vccMzwx?usp=sharing> |

**Offline use**: download `WBCA_1-8_ver2_YYYYMMDD.html` from this repository and open it in any modern browser (double-click). Everything, including the built-in reference corpora, is embedded in the file, so it works without an internet connection.

> The file name carries the build date (e.g. `20260908`). Always use the most recent file in the repository; older builds are kept only for reproducibility.

---

## 🚀 Quick Start (5 minutes)

1. **Open** the HTML file (online link above, or the downloaded file).
2. **Section 1**: choose *Auto-detect* (default), then upload a **folder** whose sub-folders are your corpora (e.g. `Move1/`, `Move2/`, `Intro/`, `Discussion/`). Plain `.txt` files are enough to start.
3. **Section 2** shows file and token counts — a quick sanity check that the corpus parsed as expected.
4. **Section 3a**: tick which folders are **Target** and which are **Reference**.
5. **Section 8a**: choose a feature type (word / lemma / n-gram / p-frame / POS-gram), select one or more keyness measures, and click **Compute**.
6. Click any row to jump to **KWIC (Section 4)** and the **Original Text (Section 5a)** for qualitative checking.
7. **Export** any table to Excel/CSV (APA 7th or MLA 9th formatting), or copy it to the clipboard.

For lemma / POS-based features (lemma, POS-gram, Word+POS, Advanced KWIC), first run your texts through the companion Colab notebook, which outputs `word_POSd_POSs_lemma` tagged text.

---

## ✨ What's New in Version 2

| Area | Version 1 | Version 2 |
|---|---|---|
| Feature types | Word-centred (with basic n-gram/p-frame support) | **Word, lemma, n-gram, p-frame, POS-gram, cluster, and Word+POS combinations**, available consistently across KWIC, frequency lists, and keyness |
| Keyness measures | Freq-LL, Text-LL, MTK | **20+ measures**: Freq-LL(2)/(4), Text-LL(2)/(4), BH q (FDR), χ² (± Yates), BIF(2)/(4), LogRatio, FreqDiff(%), Odds/Risk Ratio, MTK, ELL, Dice, Cosine, MI, CSM, McNemar, Fightin' Words z, Wilcoxon (p / BH q), rank-biserial r |
| Dispersion | Range, Juilland's D, Gries's DP | + **DP_norm, Carroll's D₂, Rosengren's S, KL divergence, DispRatio, DispBIF, DispLogR**, computed separately for the Target and Reference side |
| Reference corpus | Uploaded Reference only | + **Built-in general corpora**: BNC1994 (whole / written / spoken), BNC2014, AmE06, BE06, Brown (lower-case and mixed-case) — word/surface level |
| Multi-corpus comparison | — | **8b) Multi-Corpus Keyness**: each Target folder scored independently against one merged Reference, in a single summary table |
| Measure comparison | — | **8c) Multi-Measure Analysis** (Chujo & Utiyama 2006-style): overlap matrix, Kendall's τ correlations, top-N lists per measure, frequency-band profile |
| Lexical diversity | Token / Type / TTR | + **Guiraud's R, CTTR, Herdan's C, Maas a², Dugast's U, Brunet's W, STTR, MATTR, MTLD, HD-D, vocd-D, Yule's K / I**, lexical density |
| Collocation statistics | ~10 measures | **~24 measures** incl. MU, MS, Cohen's d, Log Ratio, log odds ratio, Fisher's Exact, Poisson-Stirling, Jaccard, Cosine, Simpson, DKL — with **CPN (Collocation Parameters Notation)** support |
| Preprocessing | Basic tokenisation | + **Number handling (4 modes), apostrophe unification, British → American spelling normalisation, editable stopword lists (spaCy / scikit-learn / Gensim / Elasticsearch / integrated), Japanese (pre-tokenised) mode, APA 7th / MLA 9th export formatting** |
| Reproducibility | — | Every table records its settings; **CPN** strings for collocations; **p-value columns** with UCREL critical values; a **Statistics reference** documenting every formula inside the tool |

---

## 🧭 Design Principles

- **One workflow, many units.** The same Target-vs-Reference logic, the same measures, and the same thresholds apply whether the unit of analysis is a word, a lemma, an n-gram, a p-frame, or a POS-gram. Results for different units are therefore directly comparable.
- **Quantitative → qualitative in one click.** Every frequency, collocation, or keyness row links back to KWIC lines and to the full original text, so statistical results can always be verified against actual usage.
- **Transparent statistics.** All formulas are documented in the in-tool Statistics reference; nothing is a black box.
- **Local-only processing.** Suitable for unpublished, learner, spoken, clinical, or otherwise sensitive corpora.

---

## 🌟 Core Functions (Sections 1–8)

| Section | Feature | Description |
|---|---|---|
| 1 | **Data Type & Upload** | Plain / Tagged modes with auto-detect; folder or multi-file upload; tokenisation, number handling, apostrophe unification, spelling normalisation, stopword customisation |
| 2 | **Corpus Summary** | Mode badge, file and token counts, sortable per-file table — an instant sanity check before analysis |
| 3 | **Corpus Overview** | 3a) Target/Reference selection per folder with descriptive statistics and lexical-diversity metrics; 3b) POS-tag distribution (Tagged mode) |
| 4 | **KWIC** | Exact / Wildcard / Regex search; Advanced `surface_POSd_POSs_lemma` patterns; positional filters (L1–L5 / node / R1–R5); colour-coded context |
| 5 | **Text Data** | 5a) full original text of any hit; 5b) concordance (dispersion) plot grouped by file or folder |
| 6 | **Collocation Analysis** | Target vs Reference collocate profiles; ~24 association measures; window, version (a/b), and C/NC thresholds mapped to CPN |
| 7 | **High-Frequency Features** | Frequency lists for any feature type; ties handling; general-corpus comparison; transpose / overlap matrix / feature profile |
| 8 | **Keyness Analysis** | 8a) standard Target-vs-Reference keyness with 20+ measures; 8b) Multi-Corpus Keyness; 8c) Multi-Measure Analysis |

This public release contains Sections 1–8. An extended research build (Sections 9 and above: frequency-table import/export, visualisation, TSV/Stanza-Biber input, multi-dimensional analysis, and other experimental analyses) exists separately; please contact the author if you are interested.)

---

## 📥 Section 1: Data Input

### Input modes

| Mode | Format | Enables |
|---|---|---|
| **Plain text** | untagged `.txt` | word / n-gram / p-frame / cluster (surface forms) |
| **Tagged** | `word_POSd_POSs_lemma` (produced by the companion [Google Colab notebook](https://colab.research.google.com/drive/1W62nqzdKbIIPpUYXsvE2ReLU3vccMzwx?usp=sharing)) | + lemma, POS, POS-gram, Word+POS features; Advanced KWIC; 3b) tag distribution |

`POSd` is the detailed (Penn Treebank-style) tag and `POSs` the simple (Universal POS) tag, e.g. `analysed_VBD_VERB_analyse`. **Auto-detect** (default) samples the first file and selects the mode automatically.

### Upload options

- **Folder upload**: each sub-folder of the selected parent folder becomes an independent corpus (e.g. `Move1`, `Move2`, or `L1`, `L2`). This is the recommended way to set up a Target/Reference design.
- **Multiple files**: files uploaded without a folder are grouped into a single virtual folder called *Ungrouped*.
- Hidden and system files (`.DS_Store`, `__MACOSX`, `Thumbs.db`, …) are excluded automatically.
- Punctuation and SPACE tokens are ignored in all counts.

### Preprocessing settings

- **P-frame settings**: position of the `*` slot(s), with a live pattern preview
- **Merge short lines**: joins subtitle- or lyrics-style fragments into paragraphs before sentence splitting
- **Word definition**: hyphen merging (`state-of-the-art` = 1 word), clitic merging (`can't`, `we'll` = 1 word), user-defined symbols, **Japanese (space-pre-tokenised) mode**
- **Unify apostrophes**: converts curly/typographic apostrophes (’ ‘ ʼ) to the straight form (`'`) so that `don't` and `don’t` are counted as one type
- **Number handling**: keep as-is / replace pure-number tokens with `#` / replace every digit with `#` / ignore pure-number tokens
- **Spelling**: optional British → American normalisation (surface forms only; lemmas are untouched)
- **Formatting Tables**: APA 7th or MLA 9th styling for Excel/CSV exports
- **Customize Stopwords**: editable lists (spaCy, scikit-learn, Gensim, Elasticsearch, or the integrated superset), selected separately for surface forms and lemmas

> ✅ The tool tells you which settings require **re-Parse** (re-reading the files) and which only require **re-Compute** (re-running the statistics), so large corpora do not have to be re-uploaded unnecessarily.

---

## 🎯 Sections 2–3: Corpus Summary & Overview

- Mode / file count / token count with a sortable per-file table (Section 2)
- Per-folder Target/Reference checkboxes (a folder may serve on both sides), "All" toggles, and drag-and-drop reordering (Section 3a)
- Descriptive statistics per folder: files, sentences, paragraphs, min / max / median / mean tokens per file, Tokens, Types, TTR
- **Compute all metrics** (with adjustable STTR / MATTR windows) adds: Guiraud's R, CTTR, Herdan's C, Maas a², Dugast's U, Brunet's W, STTR, MATTR, MTLD, HD-D, vocd-D, Yule's K / I, mean word length, mean sentence length, lexical density
- **Merge targets**: combine several folders into one Target corpus without re-uploading
- Synchronisation: Target selections are synchronised in two independent pairs (3a ↔ 8a, and 8b ↔ 8c); Reference selections are shared by all four sections
- 3b) per-folder POS-tag distribution (Tagged mode): raw / per-million-words / percentage, in either orientation

---

## 🔍 Sections 4–5: KWIC & Text Data

- **Search modes**: Exact (`cell|cells`), Wildcard (`*ing`, `b?t`), Regex (`stud(y|ies|ied)`), with a case-insensitive toggle
- **Advanced mode** (Tagged): `surface_POSd_POSs_lemma` patterns, e.g. `as_IN_ADP_*`, `*_NN|NNS_NOUN_*`, `*_*_*_analyse`
- **Display**: max lines, left / right window size, scope (Target / Reference / All / a specific folder), surface vs tagged view, colour scheme for L1–L5 / node / R1–R5
- **Positional filters**: Left / Node / Right; Exact / Partial / Wildcard / POS / POS-gram matching; single positions, ranges, and exclusions (e.g. "`the` at L1 but not `of` at L2")
- **Sorting**: by any position from L5 to R5, or by file
- **5a) Original Text**: click any KWIC line to open the full source text, colour-coded, with the hit highlighted
- **5b) Concordance Plot**: barcode-style dispersion plot grouped by file or folder; click a bar to open its KWIC lines; JPEG export

---

## 🔗 Section 6: Collocation Analysis (Target vs Reference)

- Node = a word or a p-frame (e.g. `in the *`); collocates on surface / lemma / POS; window L1–5 / R1–5
- **Statistics (~24)**: Frequency, MU, t-score, z-score, MI, MI², MI³, LL(G²)-2 / -4, LogDice, Dice, MS, Delta P (both directions), Cohen's d, Log Ratio, Log Odds Ratio, χ², Fisher's Exact, Poisson-Stirling, Log-Log, Jaccard, Cosine, Simpson, DKL / Reverse DKL
- **Version a / b**: uncorrected vs sentence-boundary-corrected window slots (Brezina 2018)
- **Thresholds**: Min score / Min C (collocate frequency) / Min NC (co-occurrence frequency)
- Settings map directly to **CPN** — e.g. `4b–MI2(3), L5–R5, C5–NC1; function words removed` (Brezina et al., 2015) — so that analyses can be reported and replicated exactly
- Target and Reference collocate lists are shown side by side, making it easy to see which collocates are specific to the Target
- 📖 The in-tool **Statistics reference** documents every formula

---

## 📈 Section 7: High-Frequency Features

- Feature types: word / lemma / n-gram / p-frame / POS-gram / cluster; `n`, number of Stars (`*`) with *exactly* / *up to* modes
- Minimum frequency per side, Top N with **ties handling** (include / exclude / strict) and tie order (alphabetical / generation)
- **General reference corpora** (built in): BNC1994 (whole 90M / written 85M / spoken 4.4M), BNC2014 (102M), AmE06 (1M), BE06 (1M), Brown (1M; lower-case or mixed-case) — word/surface level
- Stopword exclusion, word-class (function / content) filter, POS columns, search-word filter with position (All / Left / Right)
- Output columns per side: `freq`, `freq%`, `cum%`, `norm (pmw)`, `files`, `files%`; Transpose; Overlap Matrix; Feature Profile; bar-chart visualisation; Excel / CSV export

---

## 📊 Section 8: Keyness Analysis

### 8a) Standard (Target vs Reference)

Any combination of measures can be selected:

| Category | Measures |
|---|---|
| Significance (token-based) | Freq-LL(2) / (4), χ² (± Yates), **BH q** (Benjamini–Hochberg FDR-corrected) |
| Significance (text-based) | Text-LL(2) / (4), Wilcoxon p / BH q, rank-biserial r, McNemar |
| Bayesian | BIF(2) / (4) — BIC-approximated log Bayes factor (Wilson 2013) |
| Effect size | LogRatio (Hardie 2014), FreqDiff (%), Odds Ratio, Risk Ratio, ELL (Effect size for LL) |
| Association / similarity | Dice, Cosine, MI, CSM, **Fightin' Words z** (Dirichlet prior; Monroe et al. 2008) |
| Dispersion-aware | **MTK** (mean text keyness; Egbert & Biber 2019); Range, Juilland's D, DP, DP_norm, Carroll's D₂, Rosengren's S, KL; DispRatio, DispBIF, DispLogR |

- The "(2)" and "(4)" suffixes indicate whether the measure is computed from a 2-cell (Target vs Reference frequencies) or a 4-cell (full contingency) table.
- **Show p-values** adds p columns (UCREL critical values: 3.84 / 6.63 / 10.83 / 15.13 for *p* < .05 / .01 / .001 / .0001, df = 1)
- Every row links to **KWIC (4)** and **Original Text (5a)** for immediate qualitative verification
- For p-frames, filler distributions (`Fillers_T` / `Fillers_R`) are listed per frame, each filler clickable through to KWIC
- Results can be sorted by any measure and filtered by minimum frequency on either side

### 8b) Multi-Corpus Keyness (Summary Table)

- Each Target folder is scored **independently** against one merged Reference — e.g. every rhetorical move against all other moves, or every L1 group against a native-speaker corpus
- **Exclude Target from Reference** option (prevents a folder from being compared against itself when Target folders are also part of the Reference)
- The ranking measure is chosen separately from the statistics exported, so tables can be ranked by one measure and reported with several
- Filters on |stat|, |frequency|, |pmw|; Transpose; Copy (features only / with values); Excel / CSV export
- Cells click through to KWIC with the relevant folder pre-selected

### 8c) Multi-Measure Analysis

Reproduces a Chujo & Utiyama (2006)-style comparison of keyness measures on the same data:

- **Table 1 (Overlap)**: number of shared items among each measure's top-N₂ lists
- **Table 2 (Correlations)**: Kendall's τ rank-correlation matrix over the top-N₁ features
- **Table 3 (Top-N words)**: each measure's actual top-N₂ items side by side, with summary rows (average general-corpus frequency / % function words / average word length)
- **Table 4 (Freq-Band)**: distribution of the top-N₃ items across general-corpus frequency bands

This section makes it easy to see which measures favour high-frequency function words, which favour rare content words, and how far different measures agree — a useful step when choosing and justifying a measure for a study.

---

## 💾 Export

- 📋 **Copy Table** on every table (features only, or with values); pastes cleanly into Excel, Google Sheets, or Word
- Export to **Excel** (`.xlsx`) or **CSV**, with APA 7th or MLA 9th table formatting
- Concordance lines, node lists, keyness tables with all selected statistics, collocate tables, and frequency lists
- Dispersion plots and charts as JPEG

---

## 🔒 Privacy & Security

**All data processing happens locally in your browser.**

- ✅ No data is uploaded to any server (the tool makes no network requests after the page loads)
- ✅ No internet connection is required after loading the page; the downloaded file works fully offline
- ✅ Suitable for unpublished, learner, spoken, or otherwise sensitive corpora
- ✅ No account, no cookies, no tracking

---

## 🛠️ Technical Notes

- Any modern browser with ES6+ support (Chrome, Firefox, Edge, Safari); JavaScript must be enabled. Chrome or Edge are recommended for large corpora.
- The HTML file is about 23 MB because the general reference corpora (word-frequency lists) are embedded in it; the first load may take a few seconds.
- Corpus size is bounded by the browser's memory. Corpora of several million tokens work comfortably on an ordinary laptop; for tens of millions of tokens, consider splitting the corpus or closing other tabs.
- Long computations show a progress bar and can be interrupted with **Stop / Cancel**.
- Because the tool is a single self-contained file, it can be archived together with a study's data to guarantee that the exact version used remains available.

---

## 📚 Key References

- Benjamini, Y., & Hochberg, Y. (1995). Controlling the false discovery rate: A practical and powerful approach to multiple testing. *Journal of the Royal Statistical Society: Series B*, 57(1), 289–300.
- Brezina, V. (2018). *Statistics in corpus linguistics: A practical guide*. Cambridge University Press.
- Brezina, V., McEnery, T., & Wattam, S. (2015). Collocations in context: A new perspective on collocation networks. *International Journal of Corpus Linguistics*, 20(2), 139–173.
- Chujo, K., & Utiyama, M. (2006). Selecting level-specific specialized vocabulary using statistical measures. *System*, 34(2), 255–269.
- Egbert, J., & Biber, D. (2019). Incorporating text dispersion into keyword analyses. *Corpora*, 14(1), 77–104.
- Gabrielatos, C., & Marchi, A. (2012). Keyness: Appropriate metrics and practical issues. *CADS International Conference 2012*, Bologna.
- Gries, S. Th. (2008). Dispersions and adjusted frequencies in corpora. *International Journal of Corpus Linguistics*, 13(4), 403–437.
- Hardie, A. (2014). Log Ratio – an informal introduction. *CASS Briefings*. <https://cass.lancs.ac.uk/log-ratio-an-informal-introduction/>
- Larsson, T., Kim, T., & Egbert, J. (2025). Introducing and comparing two techniques for key lexical bundles analysis. *Research Methods in Applied Linguistics*, 4(3), 100245. <https://doi.org/10.1016/j.rmal.2025.100245>
- Monroe, B. L., Colaresi, M. P., & Quinn, K. M. (2008). Fightin' words: Lexical feature selection and evaluation for identifying the content of political conflict. *Political Analysis*, 16(4), 372–403.
- Paquot, M., & Bestgen, Y. (2009). Distinctive words in academic writing: A comparison of three statistical tests for keyword extraction. In A. H. Jucker, D. Schreier, & M. Hundt (Eds.), *Corpora: Pragmatics and discourse* (pp. 247–269). Rodopi.
- Wilson, A. (2013). Embracing Bayes factors for key item analysis in corpus linguistics. In M. Bieswanger & A. Koll-Stobbe (Eds.), *New approaches to the study of linguistic variability* (pp. 3–11). Peter Lang.

---

## 📌 How to Cite

**Version 2 (this tool):**

> Ishii, T. (2026). From word keyness to phraseological keyness: Version 2 of the Web-Based Corpus Analyzer (WBCA). Paper presented at the *6th Asia Pacific Corpus Linguistics Conference (APCLC 2026)*, Toyama, Japan, 8–11 September 2026. <https://smartconf.jp/host/file/paper/21598256dc134c48b9478c99cbb35b34>

**Version 1 (background and design):**

> Ishii, T. (2025). Developing Version 1 of the Web-Based Corpus Analyzer (WBCA): A browser-based corpus analysis tool with integrated workflow of KWIC, collocation, and keyness analysis. *Journal of Corpus-based Lexicology Studies*, 8, 1–20.

**Software:**

```
Ishii, T. (2026). Web-Based Corpus Analyzer (WBCA), Version 2 [Computer software].
https://ishitatu.github.io/Web-based-corpus-analyzer-VER2/
```

When reporting results, please also state the build date shown in the file name (e.g. `WBCA_1-8_ver2_20260908`) and, for collocation analyses, the CPN string displayed by the tool.

---

## 🤝 Contributing & Feedback

Bug reports, feature requests, and pull requests are welcome via [GitHub Issues](https://github.com/ishitatu/Web-based-corpus-analyzer-VER2/issues). When reporting a bug, please include the build date, your browser, the input mode (Plain / Tagged), and, if possible, a small sample that reproduces the problem.

## 📄 License

This project is licensed under the MIT License — see the LICENSE file for details.

## 🙏 Acknowledgments

- The corpus linguistics community for methodology and feedback
- The compilers of the BNC1994, BNC2014, Brown, AmE06, and BE06 corpora, whose frequency data underlie the built-in reference corpora
- Companion Google Colab notebooks for POS tagging and lemmatisation

---

**Happy corpus analyzing! 📖🔬**
