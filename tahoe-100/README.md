Tahoe-100
=========

# Overview

* **Format:** TileDB-SOMA
* **Host:** Google Cloud Storage
* **Cell count:** 100648790

## obs (cell) metadata

| Column Name                 | Description |
|-----------------------------|-------------|
| **Rowname**                 | Cell identifier |
| **sample**                  | Internal unique treatment identifier |
| **species**                 | Species genome ID |
| **gene_count**              | Number of genes with at least one count |
| **tscp_count**              | Number of transcripts, aka UMI count |
| **mread_count**             | Number of reads per cell |
| **bc1_wind**                | Internal coordinates |
| **bc2_wind**                | Internal coordinates |
| **bc3_wind**                | Internal coordinates |
| **bc1_well**                | Internal coordinates |
| **bc2_well**                | Internal coordinates |
| **bc3_well**                | Internal coordinates |
| **id**                      | Internal ID |
| **drugname_drugconc**       | Drug name, concentration, and concentration unit |
| **drug**                    | Drug name, parsed out from the `drugname_drugconc` field |
| **INT_ID**                  | Detailed Demuxlet field |
| **NUM.SNPS**                | Detailed Demuxlet field |
| **NUM.READS**               | Detailed Demuxlet field |
| **demuxlet_call**           | Demuxlet's genetic demultiplexing call (singlets are good) |
| **BEST.GUESS**              | Detailed Demuxlet field |
| **BEST.LLK**                | Detailed Demuxlet field |
| **NEXT.GUESS**              | Detailed Demuxlet field |
| **NEXT.LLK**                | Detailed Demuxlet field |
| **DIFF.LLK.BEST.NEXT**      | Detailed Demuxlet field |
| **BEST.POSTERIOR**          | Detailed Demuxlet field |
| **SNG.POSTERIOR**           | Detailed Demuxlet field |
| **cell_line**               | Cell line Cellosaurus identifier |
| **SNG.BEST.LLK**            | Detailed Demuxlet field |
| **SNG.NEXT.GUESS**          | Detailed Demuxlet field |
| **SNG.NEXT.LLK**            | Detailed Demuxlet field |
| **SNG.ONLY.POSTERIOR**      | Detailed Demuxlet field |
| **DBL.BEST.GUESS**          | Detailed Demuxlet field |
| **DBL.BEST.LLK**            | Detailed Demuxlet field |
| **DIFF.LLK.SNG.DBL**        | Detailed Demuxlet field |
| **sublibrary**              | Sublibrary ID (related to library prep and sequencing) |
| **BARCODE**                 | Barcode ID |
| **pcnt_mito**               | Percentage of mitochondrial reads |
| **S_score**                 | Inferred S phase score |
| **G2M_score**               | Inferred G2M score |
| **phase**                   | Inferred cell cycle phase |
| **cell_line_orig**          | Deprecated field |
| **pass_filter**             | Full filters are more stringent on `gene_count` and `tscp_count` |
| **cell_name**               | Commonly-used cell name (related to the `cell_line` field) |

# Tutorials

* [Python](./tutorial-py.ipynb)

# Resources

* [TileDB-SOMA](https://tiledbsoma.readthedocs.io/en/latest/index.html)
* [TileDB-SOMA Python API](https://tiledbsoma.readthedocs.io/en/latest/python-api.html)

# Contact

* [GitHub Issues](https://github.com/ArcInstitute/arc-virtual-cell-atlas/issues)