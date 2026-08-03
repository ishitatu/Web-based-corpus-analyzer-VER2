[README.md](https://github.com/user-attachments/files/30642324/README.md)
# Web-Based Corpus Analyzer (WBCA) — Version 2

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Made with HTML/CSS/JS](https://img.shields.io/badge/Made%20with-HTML%2FCSS%2FJS-orange)](https://developer.mozilla.org/en-US/docs/Web)

**From word keyness to phraseological keyness.**

WBCA Version 2 is a free, browser-based corpus linguistics tool that extends the KWIC-centred workflow of Version 1 from single words to **lemmas, n-grams, p-frames, and POS-grams**, computed under one comparable statistical setting. **All processing happens locally in your browser — no data is sent to any server.**

## 🌐 Access the Tool

- **Version 2 (this repository)**: <https://ishitatu.github.io/Web-based-corpus-analyzer-VER2/>
- **Version 1**: <https://github.com/ishitatu/Web-based-corpus-analyzer->
- **Download**: You can also download the HTML file from this repository and run it locally in your browser (no installation, no server).

---

## ✨ What's New in Version 2

| Area | Version 1 | Version 2 |
|---|---|---|
| Feature types | Word-centred (with basic n-gram/p-frame support) | **Word, lemma, n-gram, p-frame, POS-gram, cluster, and Word+POS combinations** across KWIC, frequency, and keyness |
| Keyness measures | Freq-LL, Text-LL, MTK | **20+ measures**: Freq-LL(2)/(4), Text-LL(2)/(4), BH q (FDR), χ² (±Yates), BIF(2)/(4), LogRatio, FreqDiff(%), Odds/Risk Ratio, MTK, ELL, Dice, Cosine, MI, CSM, McNemar, Fightin' Words z, Wilcoxon (p / BH q), rank-biserial r |
| Dispersion | Range, Juilland's D, Gries's DP | + **DP_norm, Carroll's D₂, Rosengren's S, KL divergence, DispRatio, DispBIF, DispLogR** (per Target/Reference side) |
| Reference corpus | Uploaded Reference only | + **Built-in general corpora**: BNC1994 (whole/written/spoken), BNC2014, AmE06, BE06, Brown (word/surface level) |
| Multi-corpus comparison | — | **8b) Multi-Corpus Keyness**: each Target folder scored independently against a merged Reference |
| Measure comparison | — | **8c) Multi-Measure Analysis** (Chujo & Utiyama 2006-style): overlap matrix, Kendall's τ correlations, top-N lists per measure, frequency-band profile |
| Lexical diversity | Token/Type/TTR | + **Guiraud's R, CTTR, Herdan's C, Maas a², Dugast's U, Brunet's W, STTR, MATTR, MTLD, HD-D, vocd-D, Yule's K/I**, lexical density |
| Collocation statistics | ~10 measures | **~24 measures** incl. MU, MS, Cohen's d, Log Ratio, log odds ratio, Fisher's Exact, Poisson-Stirling, Jaccard, Cosine, Simpson, DKL — with **CPN (Collocation Parameters Notation)** support |
| Preprocessing | Basic tokenization | + **Number handling (4 modes), British→American spelling normalisation, editable stopword lists (spaCy / scikit-learn / Gensim / Elasticsearch / integrated), APA 7th / MLA 9th export formatting** |

---

## 🌟 Core Functions (Sections 1–8)

| Section | Feature | Description |
|---|---|---|
| 1 | **Data Type & Upload** | Plain text / Tagged / TSV modes with auto-detect; folder, multi-file, or TSV/ZIP upload; tokenization, number handling, spelling normalisation, stopword customisation |
| 2 | **Corpus Summary** | Mode badge, file and token counts, sortable per-file table — an instant sanity check before analysis |
| 3 | **Corpus Overview** | 3a) Target/Reference selection per folder with descriptive statistics and lexical-diversity metrics; 3b) tag distribution (tagged/TSV) |
| 4 | **KWIC** | Exact / Wildcard / Regex search; Advanced `surface_POSd_POSs_lemma` patterns; positional filters (L1–L5 / node / R1–R5); colour-coded context |
| 5 | **Text Data** | 5a) full original text of any hit; 5b) concordance (dispersion) plot grouped by file or folder |
| 6 | **Collocation Analysis** | Target vs Reference collocate profiles; ~24 association measures; window, version (a/b), and C/NC thresholds mapped to CPN |
| 7 | **High-Frequency Features** | Frequency lists for any feature type; ties handling; general-corpus comparison; transpose / overlap matrix / feature profile |
| 8 | **Keyness Analysis** | 8a) standard Target-vs-Reference keyness with a battery of 20+ measures; 8b) Multi-Corpus Keyness; 8c) Multi-Measure Analysis |

Additional sections (9 and above) provide frequency-table import/export, visualization, and other advanced/experimental analyses.

---

## 📥 Section 1: Data Input

### Input modes

| Mode | Format | Enables |
|---|---|---|
| **Plain text** | untagged `.txt` | word / n-gram / p-frame / cluster (surface) |
| **Tagged** | `word_POSd_POSs_lemma` (via the companion [Google Colab notebook](https://colab.research.google.com/drive/1W62nqzdKbIIPpUYXsvE2ReLU3vccMzwx?usp=sharing)) | + lemma, POS, POS-gram, Word+POS features; Advanced KWIC |
| **TSV** | token/lemma/pos/xpos columns (via the companion TSV Colab notebook) | same as Tagged, from an externally parsed pipeline |

Auto-detect samples the first file and selects the mode automatically.

### Upload options

- **Folder upload**: sub-folders of the selected parent folder become independent corpora (e.g. `Move1`, `Move2`)
- **Multiple files**: grouped into a single virtual folder "Ungrouped"
- **TSV / ZIP**: multiple TSVs merged into one corpus, with optional sub-corpus split
- Hidden files (`.DS_Store`, `__MACOSX`, …) are excluded automatically; punctuation and SPACE tokens are ignored in all counts

### Preprocessing settings

- **P-frame settings**: position of `*` slots, with live pattern preview
- **Merge short lines**: joins subtitle/lyrics-style fragments into paragraphs
- **Word definition**: hyphen merging (`state-of-the-art` = 1 word), clitic merging (`can't`, `we'll` = 1 word), custom symbols, Japanese (space-pre-tokenised) mode
- **Number handling**: keep as-is / replace pure-number tokens with `#` / replace every digit with `#` / ignore pure-number tokens
- **Spelling**: optional British → American normalisation (surface forms only)
- **Formatting Tables**: APA 7th or MLA 9th styling for Excel/CSV exports
- **Customize Stopwords**: editable lists (spaCy, scikit-learn, Gensim, Elasticsearch, or the integrated superset), selected separately for surface and lemma

> ✅ The tool documents which changes need **re-Parse** and which only need **re-Compute**.

---

## 🎯 Sections 2–3: Corpus Summary & Overview

- Mode / file count / token count with a sortable per-file table (Section 2)
- Per-folder Target/Reference checkboxes (a folder may serve both sides), "All" toggles, drag-and-drop reordering (Section 3a)
- Descriptive statistics per folder: files, sentences, paragraphs, min/max/median/mean tokens, Tokens, Types, TTR
- **Re-compute metrics** (with STTR/MATTR windows) adds: Guiraud's R, CTTR, Herdan's C, Maas a², Dugast's U, Brunet's W, STTR, MATTR, MTLD, HD-D, vocd-D, Yule's K/I, mean word/sentence length, lexical density
- **Merge-targets**: group several folders into one target corpus
- Synchronisation: Target selections sync in two independent pairs (3a ↔ 8a and 8b ↔ 8c); Reference selections are shared by all four
- 3b) per-folder POS tag distribution: raw / per-million-words / percentage, two orientations

---

## 🔍 Sections 4–5: KWIC & Text Data

- **Search modes**: Exact (`cell|cells`), Wildcard (`*ing`, `b?t`), Regex (`stud(y|ies|ied)`), case-insensitive toggle
- **Advanced mode** (Tagged/TSV): `surface_POSd_POSs_lemma` patterns, e.g. `as_IN_ADP_*`, `*_NN|NNS_NOUN_*`
- **Display**: max lines, left/right window, scope (Target / Reference / All / Specific folder), surface vs tagged view, colour scheme for L1–L5 / node / R1–R5
- **Positional filters**: Left / Node / Right; Exact / Partial / Wildcard / POS / POS-gram matching; positions, ranges, and exclusions
- **5a) Original Text**: click any KWIC line to see the full source text, colour-coded
- **5b) Concordance Plot**: barcode-style dispersion, grouped by file or folder; click a bar to open its KWIC; JPEG export

---

## 🔗 Section 6: Collocation Analysis (Target vs Reference)

- Node = word or p-frame (e.g. `in the *`); collocates on surface / lemma / POS; window L1–5 / R1–5
- **Statistics (~24)**: Frequency, MU, t-score, z-score, MI, MI², MI³, LL(G²)-2/-4, LogDice, Dice, MS, Delta P (both directions), Cohen's d, Log Ratio, Log Odds Ratio, χ², Fisher's Exact, Poisson-Stirling, Log-Log, Jaccard, Cosine, Simpson, DKL / Reverse DKL
- **Version a/b**: uncorrected vs sentence-boundary-corrected window slots
- **Thresholds**: Min score / Min C (collocate frequency) / Min NC (co-occurrence frequency)
- Settings map directly to **CPN** — e.g. `4b–MI2(3), L5–R5, C5–NC1; function words removed` (Brezina et al., 2015) — for reproducible reporting
- 📖 In-tool **Statistics reference** documents every formula

---

## 📈 Section 7: High-Frequency Features

- Feature types: word / lemma / n-gram / p-frame / POS-gram / cluster; `n`, Stars (`*`) with *exactly* / *up to* modes
- Min freq per side, Top N with **ties handling** (include / exclude / strict) and tie order (alphabetical / generation)
- **General reference corpora**: BNC1994 (whole / written / spoken), BNC2014, AmE06, BE06, Brown (word/surface)
- Stopword exclusion, word-class (function/content) filter, POS columns, search-word filter with position (All / Left / Right)
- Output: `freq`, `freq%`, `cum%`, `norm (pm)`, `files`, `files%` per side; Transpose; Overlap Matrix; Feature Profile; bar-chart visualization; Excel/CSV export

---

## 📊 Section 8: Keyness Analysis

### 8a) Standard (Target vs Reference)

Measures (select any combination):

| Category | Measures |
|---|---|
| Significance (token-based) | Freq-LL(2)/(4), χ² (±Yates), **BH q** (FDR-corrected) |
| Significance (text-based) | Text-LL(2)/(4), Wilcoxon p / BH q, rank-biserial r, McNemar |
| Bayesian | BIF(2)/(4) (BIC-approximated log Bayes factor) |
| Effect size | LogRatio, FreqDiff(%), OddsRatio, RiskRatio, ELL |
| Association / similarity | Dice, Cosine, MI, CSM, **Fightin' Words z** (Dirichlet prior) |
| Dispersion-aware | **MTK**; Range, Juilland's D, DP, DP_norm, Carroll's D₂, Rosengren's S, KL; DispRatio, DispBIF, DispLogR |

- **Show p-values** adds p columns (UCREL critical values: 3.84 / 6.63 / 10.83 / 15.13 for *p* < .05 / .01 / .001 / .0001, df = 1)
- Every row links to **KWIC (4)** and **Original Text (5a)** for immediate qualitative verification
- P-frame filler distributions (`Fillers_T` / `Fillers_R`) with click-through to KWIC

### 8b) Multi-Corpus Keyness (Summary Table)

- Each Target folder scored **independently** against one merged Reference
- **Exclude Target from Reference** option; ranking measure chosen separately from export statistics
- Filters on |stat|, |frequency|, |pmw|; Transpose; Copy (features only / with values); Excel/CSV export
- Cells click through to KWIC with the folder pre-selected

### 8c) Multi-Measure Analysis

Reproduces a Chujo & Utiyama (2006)-style comparison across measures:

- **Table 1 (Overlap)**: shared items among each measure's top-N₂ lists
- **Table 2 (Correlations)**: Kendall's τ rank-correlation matrix over top-N₁ features
- **Table 3 (Top-N words)**: each measure's actual top-N₂ items side by side, with summary rows (Avg GC freq / % function words / Avg word length)
- **Table 4 (Freq-Band)**: distribution of top-N₃ items across general-corpus frequency bands

---

## 💾 Export

- 📋 Copy Table (TSV) throughout; Export to **Excel** / **CSV** (APA 7th or MLA 9th formatting)
- Concordance lines and node lists; keyness tables with all selected statistics; collocate tables; frequency lists
- Dispersion plots and charts as JPEG

---

## 🔒 Privacy & Security

**All data processing happens locally in your browser.**

- ✅ No data is uploaded to any server
- ✅ No internet connection required after loading the page
- ✅ Suitable for unpublished, learner, spoken, or otherwise sensitive corpora

---

## 🛠️ Technical Notes

- Modern browsers with ES6+ support (Chrome, Firefox, Edge, Safari); JavaScript required
- Large corpora (tens of millions of tokens) are bounded by browser memory — consider splitting very large corpora
- Progress bars and Stop/Cancel buttons for long computations

---

## 📚 Key References

- Benjamini, Y., & Hochberg, Y. (1995). Controlling the false discovery rate. *Journal of the Royal Statistical Society: Series B*, 57(1), 289–300.
- Brezina, V. (2018). *Statistics in corpus linguistics: A practical guide.* Cambridge University Press.
- Brezina, V., McEnery, T., & Wattam, S. (2015). Collocations in context: A new perspective on collocation networks. *International Journal of Corpus Linguistics*, 20(2), 139–173.
- Chujo, K., & Utiyama, M. (2006). Selecting level-specific specialized vocabulary using statistical measures. *System*, 34(2), 255–269.
- Egbert, J., & Biber, D. (2019). Incorporating text dispersion into keyword analyses. *Corpora*, 14(1), 77–104.
- Gabrielatos, C., & Marchi, A. (2012). Keyness: Appropriate metrics and practical issues. *CADS International Conference 2012*.
- Hardie, A. (2014). Log Ratio – an informal introduction. *CASS Briefings*. <https://cass.lancs.ac.uk/log-ratio-an-informal-introduction/>
- Larsson, T., Kim, T., & Egbert, J. (2025). Introducing and comparing two techniques for key lexical bundles analysis. *Research Methods in Applied Linguistics*, 4(3), 100245. <https://doi.org/10.1016/j.rmal.2025.100245>
- Monroe, B. L., Colaresi, M. P., & Quinn, K. M. (2008). Fightin' words. *Political Analysis*, 16(4), 372–403.
- Paquot, M., & Bestgen, Y. (2009). Distinctive words in academic writing. In *Corpora: Pragmatics and discourse* (pp. 247–269). Rodopi.
- Wilson, A. (2013). Embracing Bayes factors for key item analysis in corpus linguistics. In *New approaches to the study of linguistic variability* (pp. 3–11). Peter Lang.

## 📌 Suggested Citation

> Ishii, T. (2025). Developing Version 1 of the Web-Based Corpus Analyzer (WBCA): A browser-based corpus analysis tool with integrated workflow of KWIC, collocation, and keyness analysis. *Journal of Corpus-based Lexicology Studies*, 8, 1–20.

```
Web-Based Corpus Analyzer (WBCA), Version 2. [Software].
Available at: https://ishitatu.github.io/Web-based-corpus-analyzer-VER2/
```

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## 📄 License

This project is licensed under the MIT License — see the LICENSE file for details.

## 🙏 Acknowledgments

- The corpus linguistics community for methodology and feedback
- Companion Google Colab notebooks for POS tagging and TSV generation

---

**Happy corpus analyzing! 📖🔬**
