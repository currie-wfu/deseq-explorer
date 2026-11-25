# DESeq2 gene explorer

A single-page, in-browser explorer for DESeq2 results. Load one or more result files, search by gene name, and see log2 fold change, adjusted p-value and per-sample normalized counts across all your comparisons at once.

**Open it:** https://currie-wfu.github.io/deseq-explorer/

Your files are read locally by your browser. Nothing is uploaded, and no data is stored on this site.

## Using it

1. Open the page and click **Open files…** or **Open folder…**, or drag files onto it. Each file (CSV or TSV) is one comparison.
2. Type gene names, separated by commas, spaces or new lines. Use `*` as a wildcard, for example `HOX*`.
3. Set the highlight cutoffs (padj and |log2FC|), and optionally hide genes with low baseMean.
4. Click **Download CSV** to export the genes you are looking at.

The loaded data is remembered in your browser, so it is still there next time. **Remove all files** clears it.

## Expected file format

Columns are matched by header name, in any order. Matching ignores case and punctuation.

| What | Recognised headers |
| --- | --- |
| Gene (required) | `gene`, `gene_id`, `gene_name`, `symbol`, `id`, a blank header (R row names), or else the first column |
| log2 fold change (required) | `log2FoldChange`, `log2FC`, `logFC` |
| Adjusted p-value | `padj`, `FDR`, `qvalue` |
| Other statistics | `baseMean`, `pvalue`, `lfcSE`, `stat` |
| Sample counts (optional) | any other numeric column |

Sample groups are guessed from the sample column names (for example `rep1_Treated_day3` and `rep1_Control_day3` give Treated and Control). You can rename comparisons, reorder them, and edit or exclude samples under **Edit sample groups**. Files without sample columns still work; the table and plots then show the statistics only.

Notes:
- The sign of log2FC follows the contrast used when the file was made. The page cannot tell which group is the numerator.
- Counts are plotted as they appear in the file, so mixing normalized and raw counts across files puts them on different scales.
- Numeric columns that are not samples (for example gene length or an Entrez ID) are read as samples. Clear their group under **Edit sample groups** to leave them out.

## Running it offline

Download `index.html` and open it in any modern browser. It has no dependencies and needs no internet connection.

## License

MIT. See [LICENSE](LICENSE).
