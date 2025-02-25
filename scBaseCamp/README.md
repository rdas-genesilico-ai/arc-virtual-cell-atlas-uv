scBaseCamp
==========

### Reprocessing of 10X Genomics scRNA-seq datasets available from the Sequence Read Archive.

<a href="https://arcinstitute.org/manuscripts//scBaseCamp">
  <img src="./img/scBaseCamp_banner.jpg" alt="scBaseCamp" width="780" height="415">
</a>


# Overview

scBaseCamp is a continuously updated single-cell RNA-seq database that employs an AI-driven, hierarchical agent workflow to automate discovery, metadata extraction, and standardized preprocessing of Sequence Read Archive (SRA) data.

Currently the largest public repository of single-cell data comprising over 200 million cells (and expanding), spanning 21 organisms and 72 tissues.

By continually discovering, annotating, and reprocessing raw single-cell RNA-seq data, scBaseCamp offers an expansive and harmonized repository that can serve as a foundation for AI-driven modeling and integrative meta-analyses.


# Dataset location

All data is located on a Google Cloud Storage bucket at `gs://arc-ctc-scbasecamp`.

See the tutorials below on progamatically accessing the data.

You can also directly download the data with the [gsutil tool](https://cloud.google.com/storage/docs/gsutil).
Please be mindful of the egress costs associated with downloading data from Google Cloud Storage (costs to the Arc Institute).


# Releases

## 2025-02-01: Initial release

#### Statistics

* \>230 million cells
* 21 organisms
* Multiple STARsolo count features (e.g., `Gene`, `GeneFull_Ex50pAS`, and `Velocyto`)
  * Note: only `filtered` count tables are provided (no `raw`)

#### Metadata

The observation metadata was obtained via [SRAgent](https://github.com/ArcInstitute/SRAgent).

#### Sample Metadata (SRX accession level)

Each sample includes the following metadata fields:

**Core Identifiers**
* `entrez_id`: Entrez database identifier
* `srx_accession`: SRA experiment accession
* `file_path`: Path to h5ad file in Google Cloud Storage
* `obs_count`: Total number of cells/observations

**Technical Information**
* `lib_prep`: Library preparation method (10X Genomics or other)
* `tech_10x`: Specific 10X Genomics technology (3' or 5')
* `cell_prep`: Sample preparation type (single nucleus or single cell)

**Biological Information**
* `organism`: Species of origin
* `tissue`: Source tissue
* `disease`: Disease status (if applicable)
* `purturbation`: Experimental perturbations (if applicable)
* `cell_line`: Cell line information (if applicable)

**Collection Information**
* `czi_collection_id`: CZI collection identifier (if applicable)
* `czi_collection_name`: CZI collection name (if applicable)

#### Cell-level Metadata (per observation)

Each individual cell (obs) contains:
* `gene_count`: Number of unique genes detected
* `umi_count`: Total number of Unique Molecular Identifiers (UMIs)

#### STARsolo Count Features

* **Gene:** Counts reads mapping entirely to exonic regions of annotated transcripts, capturing fully spliced
transcripts. This procedure represents traditional gene expression analyses and was the default in earlier
CellRanger versions.
* **GeneFull:** Counts reads overlapping entire gene locus, i.e. including exonic and intronic regions. This
captures both unspliced (primary) and spliced transcripts and providing a more comprehensive view of
gene activity.
* **GeneFull_ExonOverIntron:** Counts reads overlapping exonic and intronic regions, but assigns higher
priority to exonic overlaps. This option helps to resolve reads that map to overlapping genes.
* **GeneFull_Ex50pAS:** Similar to the above option, but with more sophisticated priorities scheme, which
prioritizes partial and antisense exonic overlap over intronice reads.
* **Velocyto:** Generates separate count matrices for spliced, unspliced, and ambiguous reads, following
the rules from ([La Manno et al., 2018](https://doi.org/10.1038/s41586-018-0414-6)). 
This enables RNA velocity analyses to infer dynamic cellular processes.

#### Notes

* Currently, the dataset does NOT include cell type annotations.
  * We are looking into scalable approaches to annotate cell types across the entire dataset.
  * This task is not trivial, given the diversity of the dataset (e.g., organisms and tissues).
* STARsolo count features (e.g., `Gene`, `GeneFull_Ex50pAS`, and `Velocyto`)
  * `GeneFull*` will have more counts than `Gene` due to the mapping algorithm.
  * `Velocyto` h5ad files include 3 layers: `spliced`, `unspliced`, and `ambiguous`.
     * The `X` matrix is `spliced` matrix, in addition to the `spliced` layer.
  * `unique` mapping is used for all count features.
    * `EM` and `uniform` mapping will be added soon.
    * However, we have found that `unique` mapping is the best choice for at least most datasets.
* We are currently not using [TileDB-SOMA](https://tiledbsoma.readthedocs.io/en/latest/index.html)
  due to some challenges with scaling, but we are actively working on this.



# Tutorials

* [Python tutorial](./tutorial-py.ipynb)
* [R tutorial](./tutorial-R.ipynb)


# Resources

* [Arc Institute](https://arcinstitute.org)


# Contact

* [GitHub Issues](https://github.com/ArcInstitute/arc-virtual-cell-atlas/issues)


# Citation

TODO