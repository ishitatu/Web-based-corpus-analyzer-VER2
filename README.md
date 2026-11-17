# Web-Based Corpus Analyzer (WBCA) — Version 2

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Made with HTML/CSS/JS](https://img.shields.io/badge/Made%20with-HTML%2FCSS%2FJS-orange)](https://developer.mozilla.org/en-US/docs/Web)
[![Runs in browser](https://img.shields.io/badge/Runs-100%25%20in%20browser-brightgreen)](#-privacy--security)

**From word keyness to phraseological keyness.**

WBCA Version 2 is a free, open-source, browser-based corpus linguistics tool. It extends the KWIC-centred workflow of Version 1 from single words to **lemmas, n-grams, p-frames, and POS-grams**, so that word-level and phrase-level keyness can be computed and compared under one consistent statistical setting. The whole tool is a **single HTML file**: there is nothing to install, no server, and no account. **All processing happens locally in your browser — your texts are never sent anywhere.**

---

## 🌐 Access the Tool

| | Link |
|---|---|
| **▶ Run WBCA in your browser** (always opens the latest build) | <https://ishitatu.github.io/Web-based-corpus-analyzer-VER2/> |
| **Latest build — HTML file (view / download)** | <https://github.com/ishitatu/Web-based-corpus-analyzer-VER2/blob/main/WBCA_1-8_ver2-20261124.html> |
| **Demo corpus** (two tagged corpora, ZIP) | <https://github.com/ishitatu/Web-based-corpus-analyzer-VER2/blob/main/WBCA%20Demo%20corpus%202.zip> |
| **Google Site (documentation + embedded tool)** | <https://sites.google.com/view/web-basedcorpusanalyzerver2/> |
| **This repository** | <https://github.com/ishitatu/Web-based-corpus-analyzer-VER2> |
| **Version 1** | <https://github.com/ishitatu/Web-based-corpus-analyzer-> |
| **Companion Google Colab notebook (POS tagging / lemmatisation)** | <https://colab.research.google.com/drive/1W62nqzdKbIIPpUYXsvE2ReLU3vccMzwx?usp=sharing> |

**Latest build:** `WBCA_1-8_ver2-20261124.html`. To open exactly this build (for example, in a citation), use <https://ishitatu.github.io/Web-based-corpus-analyzer-VER2/WBCA_1-8_ver2-20261124.html>.

**Offline use**: open the HTML file page above, click **Download raw file** (the ⬇ icon at the top right of the file view), and open the downloaded `WBCA_1-8_ver2-YYYYMMDD.html` in any modern browser (double-click). The GitHub file page itself only shows the file (it is too large to preview), so use the GitHub Pages link to run the tool online. Everything, including the built-in reference corpora, is embedded in the file, so it works without an internet connection (the one exception is the optional kuromoji analyser for Japanese; see [Privacy & Security](#-privacy--security)).

> The file name carries the build date (e.g. `20261124`). The repository holds the latest build; earlier builds remain in the [commit history](https://github.com/ishitatu/Web-based-corpus-analyzer-VER2/commits/main) for reproducibility (open a commit and choose **Browse files**).

---

## 🚀 Quick Start (5 minutes)

1. **Open** WBCA (the link above, or the downloaded file).
2. **Section 1**: leave *Data Type* on **Auto-detect** (default) and choose a **folder** under *Folder upload* whose sub-folders are your corpora (e.g. `Move1/`, `Move2/`, `Intro/`, `Discussion/`). Plain `.txt` files are enough to start. Then click **Load & Parse Corpus**. (Some browsers ask whether to "upload" the folder; the files are only read inside your browser.)
3. **Section 2** shows the mode (Plain text / Tagged corpus) and the file and token counts — a quick sanity check that the corpus parsed as expected.
4. **Section 3a**: tick which folders are **Target** and which are **Reference**.
5. **Section 8a**: choose a feature type (word / lemma / n-gram / p-frame / POS-gram, …), tick one or more keyness measures, and click **Compute Keyness / Frequency**.
6. Click any row to see its concordance lines in **KWIC (Section 4)**; click a KWIC line to read the whole text in **Original Text (Section 5a)**.
7. **Copy** any table to the clipboard, or **export** it to Excel / CSV (APA 7th or MLA 9th formatting available).

**Try it with the demo corpus**: download `WBCA Demo corpus 2.zip` (link above), unzip it, and choose the folder `WBCA Demo corpus` in step 2. It holds two tagged corpora of lecture transcripts — `Harvard-psychology` (22 files) and `The Ethics of Technological Disruption` (6 files) — so lemma and POS features work as well. For example, set `Harvard-psychology` as Target and `The Ethics of Technological Disruption` as Reference.

For lemma / POS-based features (lemma, POS-gram, Word+POS, Advanced KWIC), first run your texts through the companion Colab notebook, which outputs `word_POSd_POSs_lemma` tagged text.

---

## ✨ What's New in Version 2

| Area | Version 1 | Version 2 |
|---|---|---|
| Feature types | Word-centred (with basic n-gram/p-frame support) | **Word (surface / lemma), n-gram, p-frame, cluster, POS and POS-gram (simple / detailed), and Word / n-gram + POS combinations** for frequency lists and keyness; KWIC, concordance plots, and collocation search words, lemmas, n-grams, p-frames, POS tags, and POS-grams |
| Keyness measures | Freq-LL, Text-LL, MTK | **20+ measures**: Freq-LL(2)/(4), Text-LL(2)/(4), BH q (FDR), χ² (± Yates), BIF(2)/(4), LogRatio, FreqDiff(%), Odds/Risk Ratio, MTK, ELL, Dice, Cosine, MI, CSM, McNemar, Fightin' Words z, Wilcoxon (p / BH q), rank-biserial r |
| Dispersion | Range, Juilland's D, Gries's DP | + **DP_norm, Carroll's D₂, Rosengren's S, KL divergence, DispRatio, DispBIF, DispLogR**, computed separately for the Target and Reference side |
| Reference corpus | Uploaded Reference only | + **Built-in general corpora**: BNC1994 (whole / written / spoken), BNC2014, AmE06, BE06, Brown (lower-case and mixed-case) — word/surface level |
| Multi-corpus comparison | — | **8b) Multi-Corpus Keyness**: each Target folder scored independently against one merged Reference, in a single summary table, with an overlap matrix and a feature profile across corpora |
| Measure comparison | — | **8c) Multi-Measure Analysis** (Chujo & Utiyama 2006-style): overlap matrix, Kendall's τ correlations, top-N lists per measure, frequency-band profile |
| Lexical diversity | Token / Type / TTR | + **Guiraud's R, CTTR, Herdan's C, Maas a², Dugast's U, Brunet's W, STTR, MATTR, MTLD, HD-D, vocd-D, Yule's K / I**, lexical density |
| Collocation statistics | ~10 measures | **26 statistics** incl. MU, MS, Cohen's d, Log Ratio, log odds ratio, Fisher's Exact, Poisson-Stirling, Tanimoto (numeric Jaccard), Cosine, Simpson, DKL — with **CPN (Collocation Parameters Notation)** support |
| Preprocessing | Basic tokenisation | + **Three word-definition modes, number handling (4 modes), apostrophe and hyphen unification, British ↔ American spelling normalisation, editable stopword lists (English and Japanese), Japanese corpus mode, APA 7th / MLA 9th export formatting** |
| Reproducibility | — | Every Excel export includes a **settings sheet**; **settings profiles** (JSON) can be saved and loaded; **CPN** strings for collocations; **p-value columns** with UCREL critical values; a **Statistics reference** documenting every formula inside the tool |

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
| 1 | **Data Type & Upload** | Plain / Tagged modes with auto-detect; folder or multi-file upload; word definition and tokenisation, number handling, apostrophe and hyphen unification, spelling normalisation, stopword customisation, Japanese corpus mode |
| 2 | **Corpus Summary** | Mode badge, file, token, and type counts, sortable per-file table — an instant sanity check before analysis |
| 3 | **Corpus Overview** | 3a) Target/Reference selection per folder with descriptive statistics, lexical-diversity metrics, and charts; 3b) POS-tag distribution (Tagged mode) |
| 4 | **KWIC** | Exact / Wildcard / Regex search on words, lemmas, n-grams, p-frames, POS tags, and POS-grams; Advanced `surface_POSd_POSs_lemma` patterns; positional filters (L1–L5 / node / R1–R5); colour-coded context |
| 5 | **Text Data** | 5a) full original text of any hit; 5b) concordance (dispersion) plot grouped by file or folder |
| 6 | **Collocation Analysis** | Target vs Reference collocate profiles; 26 statistics; window, window boundary, exposure correction (a/b), and C/NC thresholds mapped to CPN |
| 7 | **High-Frequency Features** | Frequency lists for any feature type; ties handling; general-corpus comparison; filters; bar charts |
| 8 | **Keyness Analysis** | 8a) standard Target-vs-Reference keyness with 20+ measures; 8b) Multi-Corpus Keyness; 8c) Multi-Measure Analysis |

This public release contains Sections 1–8. An extended research build (Sections 9 and above: frequency-table import/export, visualisation, TSV/Stanza-Biber input, multi-dimensional analysis, and other experimental analyses) exists separately; please contact the author if you are interested.

---

## 📥 Section 1: Data Input

### Input modes

| Mode | Format | Enables |
|---|---|---|
| **Plain text** | untagged `.txt` | word / n-gram / p-frame / cluster (surface forms) |
| **Tagged** | `word_POSd_POSs_lemma` (produced by the companion [Google Colab notebook](https://colab.research.google.com/drive/1W62nqzdKbIIPpUYXsvE2ReLU3vccMzwx?usp=sharing)) | + lemma, POS, POS-gram, Word+POS, and n-gram+POS features; Advanced KWIC; 3b) tag distribution |
| **Japanese** | plain Japanese text with **Japanese corpus** ticked, or tagged Japanese `word_POS` | word boundaries from spaces (already segmented text), the browser's own word segmenter, or kuromoji (which also adds POS and base forms) |

`POSd` is the detailed (Penn Treebank-style) tag and `POSs` the simple (Universal POS) tag, e.g. `analysed_VBD_VERB_analyse`. **Auto-detect** (default) samples the first file and selects the mode automatically.

### Upload options

- **Folder upload**: each sub-folder of the selected parent folder becomes an independent corpus (e.g. `Move1`, `Move2`, or `L1`, `L2`). This is the recommended way to set up a Target/Reference design.
- **Multiple files**: files uploaded without a folder are grouped into a single virtual folder called *Ungrouped*.
- Hidden files (`.DS_Store`, `__MACOSX`, …), system files (`Thumbs.db`, `desktop.ini`, …), empty files, and non-text files (`.docx`, `.pdf`, images, …) are left out automatically, and WBCA lists what it left out.
- Text files should be UTF-8 (with or without BOM) or UTF-16 with BOM; other files are read as Shift_JIS (when they look Japanese) or Windows-1252, with a warning.
- Punctuation and SPACE tokens are not counted as words.

### Preprocessing settings

- **P-frame settings**: whether the `*` slot may stand at the first / last position, with a live pattern preview
- **Merge short lines**: joins subtitle- or lyrics-style fragments into paragraphs before sentence splitting
- **Sentences and abbreviations**: editable sentence-ending marks; an editable list of abbreviations (`Fig.`, `U.S.`, `et al.`) kept as one word; n-grams, p-frames, and POS-grams can respect sentence boundaries
- **Word definition**: three modes (Default, Word-character based, Custom regex); hyphen joining (`state-of-the-art` = 1 word), apostrophe joining (`can't`, `we'll` = 1 word), user-defined symbols
- **Unify apostrophes / hyphens**: converts typographic apostrophes (’ ‘ ʼ ＇) to `'` so that `don't` and `don’t` are counted as one type, and hyphen variants (‐ ‑ －) to `-`; dashes and minus signs optionally too
- **Number handling**: keep as-is / replace pure-number tokens with `#` / replace every digit with `#` / ignore pure-number tokens
- **Spelling**: optional British → American or American → British normalisation (surface forms only; lemmas are untouched)
- **Japanese corpus**: word boundaries Auto / Spaces / Browser segmenter / kuromoji; the segmented (or kuromoji-tagged) text can be downloaded as `.txt` files and loaded again later
- **Formatting Tables**: APA 7th, MLA 9th, or plain (User edition) styling for Excel/CSV exports, with an optional title and note; formatted tables can also be saved as HTML
- **Customize Stopwords**: editable lists for English (Integrated ★, Gensim, spaCy, scikit-learn, Function words (short contexts), Elasticsearch-default) and Japanese (Integrated, Function words, spaCy-ja, stopwords-iso-ja), selected separately for surface forms and lemmas, plus function-word lists used by the *Word class* filter

> ✅ Each setting states when it takes effect — when the corpus is loaded (**Load & Parse Corpus**), with **Apply**, or at the next **Compute** — and Apply rebuilds the word units in place, so large corpora do not have to be re-uploaded.

> 💾 **Settings profile**: **Save** / **Load** at the top of the page store every on-screen setting (including Target/Reference choices and stopword lists) as a JSON file, so an analysis can be set up again exactly. The corpus itself is not stored.

---

## 🎯 Sections 2–3: Corpus Summary & Overview

- Mode / file count / token and type counts with a sortable per-file table (Section 2)
- Per-folder Target/Reference checkboxes (a folder may serve on both sides), "All" toggles, and drag-and-drop reordering (Section 3a); the folder order is shared with 8a–8c
- Descriptive statistics per folder: files, sentences, paragraphs, min / max / median / mean tokens per file, Tokens, Types, TTR, sentence and word length (min / max / median / mean / SD); in Tagged mode also lemma tokens / types / TTR and lexical density
- **Compute lexical-diversity stats** or **⚙ Compute all metrics** (with adjustable STTR / MATTR windows) adds: Guiraud's R, CTTR, Herdan's C, Maas a², Dugast's U, Brunet's W, STTR, MATTR, MTLD, HD-D, vocd-D, Yule's K / I
- **Normalized frequency**: per 100 … 10,000,000 words (default: per million), used by 3b, 7, 8a, and 8b
- **Merge targets**: combine several folders into one Target corpus without re-uploading
- Synchronisation: Target selections are synchronised in two independent pairs (3a ↔ 8a, and 8b ↔ 8c); Reference selections are shared by all four sections
- 📊 Charts for 3a: bar chart, TTR growth curve, box plot, radar, heatmap, pie chart
- 3b) per-folder POS-tag distribution (Tagged mode): raw / normalised / percentage of folder tokens, in either orientation, with stacked-bar, heatmap, and pie charts

---

## 🔍 Sections 4–5: KWIC & Text Data

- **Search modes**: Exact (`cell|cells`), Wildcard (`*ing`, `b?t`), Regex (`stud(y|ies|ied)`), with a case-insensitive toggle; feature types word / lemma / n-gram / p-frame / POS / POS-gram / Regex
- **Advanced mode** (Tagged): `surface_POSd_POSs_lemma` patterns, e.g. `as_IN_ADP_*`, `*_NN|NNS_NOUN_*`, `*_*_*_analyse`
- **Display**: max lines, left / right window size, scope (Target / Reference / All / specific folders), surface vs tagged view, colour scheme for L1–L5 / node / R1–R5
- **Positional filters**: Left / Node / Right; Exact / Partial / Wildcard / POS / POS-gram matching; single positions, ranges, and exclusions (e.g. "`the` at L1 and no noun at R1")
- **Sorting**: by the N-th word on the left, the node, or the right (A→Z / Z→A), or by the Folder / File columns
- **Export**: copy lines or nodes; Excel / CSV with all hits
- **5a) Original Text**: click any KWIC line to open the full source text, colour-coded, with the hit highlighted
- **5b) Concordance Plot**: barcode-style dispersion plot grouped by file or folder; click a bar to open its KWIC lines; copy, or save as JPEG / SVG (optionally black & white)

---

## 🔗 Section 6: Collocation Analysis (Target vs Reference)

- Node = a word, lemma, n-gram, p-frame (e.g. `in the *`), POS tag / POS-gram, or regex, or an Advanced-mode pattern synced with KWIC; collocates counted as surface / lemma / POS (simple / detailed); window L1–5 / R1–5
- **Window boundary**: whole file / line breaks / sentence-ending marks / sentence-ending marks plus `;` `:` / any punctuation
- **Statistics (26)**: Frequency, MU, t-score, z-score, MI, MI², MI³, LL(G²)-2 / -4, LogDice, Dice, MS, Delta P (both directions), Cohen's d, Log Ratio, Log Odds Ratio, χ², Fisher's Exact, Poisson-Stirling, Log-Log, Tanimoto (numeric Jaccard), Cosine, Simpson, DKL / Reverse DKL contribution
- **Exposure correction**: Uncorrected (*a*: node frequency) vs Corrected (*b*: the context slots that remain within the window boundary)
- **Thresholds**: Min score / Min C (collocate frequency) / Min NC (co-occurrence frequency); **Collocate POS filter** (UD or Penn Treebank tags)
- Settings map directly to **CPN**, shown under the results — e.g. `4b–MI2(3), L5–R5, C5–NC1; POS simple: NOUN/VERB/ADJ` (Brezina et al., 2015) — so that analyses can be reported and replicated exactly
- Target and Reference collocate lists are shown side by side (all positions and each of L5…R5), making it easy to see which collocates are specific to the Target; click a collocate to narrow the KWIC lines
- 📖 The in-tool **Statistics reference** documents every formula

---

## 📈 Section 7: High-Frequency Features

- Feature types: word / lemma / n-gram / p-frame / cluster / POS / POS-gram, and Word or n-gram + POS combinations; `n`, number of Stars (`*`) with *exactly* / *up to* modes
- Minimum frequency per side, minimum range (files), Top N with **ties handling** (include / exclude / strict) and tie order (alphabetical / generation)
- **General reference corpora** (built in): BNC1994 (whole 90M / written 85M / spoken 4.4M), BNC2014 (102M), AmE06 (1M), BE06 (1M), Brown (1M; lower-case or mixed-case) — word/surface level
- Stopword exclusion, word-class (function / content) filter, POS columns and POS filter, feature filter, search-word filter with position (Any / Left / Right)
- Output columns per side: `freq`, `freq%`, `cum%`, `norm` (per million by default), `range`, `range%`; delete / restore rows; bar charts; Excel / CSV export

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
- Click a row to open its lines in **KWIC (4)**, and a KWIC line to open the **Original Text (5a)**, for immediate qualitative verification
- For p-frames, filler distributions (`Fillers_T` / `Fillers_R`) are listed per frame, each filler clickable through to KWIC
- Results can be sorted by any measure, limited by the Target frequency (Min freq (fT)), and narrowed with stopword, word-class, feature, and POS filters; rows can be deleted from the table and its exports

### 8b) Multi-Corpus Keyness (Summary Table)

- Each Target folder is scored **independently** against one merged Reference (or a built-in general corpus) — e.g. every rhetorical move against all other moves, or every L1 group against a native-speaker corpus
- **Exclude Target from Reference** option (prevents a folder from being compared against itself when Target folders are also part of the Reference)
- The ranking measure is chosen separately from the statistics exported, so tables can be ranked by one measure and reported with several
- Filters on |stat|, |frequency|, |norm| (dim the other cells, or leave them out and rank again); Transpose; Copy (features only / with values); Excel / CSV export
- **Overlap Matrix** (shared top-N features between corpora) and **Feature Profile** (one feature looked up across all corpora)
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

- 📋 **Copy Table** on every table (8b: features only, or with values); pastes cleanly into Excel, Google Sheets, or Word
- Export to **Excel** (`.xlsx`) or **CSV**, with APA 7th / MLA 9th / plain table formatting; every Excel file also contains a `setting` sheet recording the settings used
- Concordance lines, node lists, keyness tables with all selected statistics, collocate tables, and frequency lists
- Figures (concordance plots and charts) as JPEG or SVG, optionally in black & white, or copied to the clipboard

---

## 🔒 Privacy & Security

**All data processing happens locally in your browser.**

- ✅ Your texts are never uploaded to any server. The tool makes no network requests after the page loads, with one opt-in exception: choosing *Word boundaries = kuromoji* for a Japanese corpus downloads the kuromoji analyser and its dictionary from `cdn.jsdelivr.net` (the texts themselves are still analysed in your browser)
- ✅ No internet connection is required after loading the page; the downloaded file works fully offline (without a connection, a Japanese corpus is split with the browser's own word segmenter instead of kuromoji)
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

When reporting results, please also state the build date shown in the file name (e.g. `WBCA_1-8_ver2-20261124`) and, for collocation analyses, the CPN string displayed by the tool. The `setting` sheet of each Excel export records the file name and the settings used.

---

## 🤝 Contributing & Feedback

Bug reports, feature requests, and pull requests are welcome via [GitHub Issues](https://github.com/ishitatu/Web-based-corpus-analyzer-VER2/issues). When reporting a bug, please include the build date, your browser, the input mode (Plain / Tagged), and, if possible, a settings profile (**Save** at the top of the page) and a small sample that reproduces the problem.

## 📄 License

This project is licensed under the MIT License — see the LICENSE file for details.

## 🙏 Acknowledgments

- The corpus linguistics community for methodology and feedback
- The compilers of the BNC1994, BNC2014, Brown, AmE06, and BE06 corpora, whose frequency data underlie the built-in reference corpora
- Companion Google Colab notebooks for POS tagging and lemmatisation
- Open-source software used in the tool: SheetJS (Excel export, built into the file), kuromoji.js (optional Japanese analysis), and the stopword lists of spaCy, scikit-learn, Gensim, Elasticsearch, and stopwords-iso

---

**Happy corpus analyzing! 📖🔬**
