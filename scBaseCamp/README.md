scBaseCamp
==========

![scBaseCamp](./img/scBaseCamp1.png)

Reprocessing of 10X Genomics scRNA-seq datasets available from the Sequence Read Archive.

# Dataset summary

## obs (cell) metadata

# Reprocessing overview

## Find the datasets

* LLM agents used to find the target 10X Genomics scRNA-seq datasets in the SRA and gather specific metadata.
  * Agent framwork: [langgraph](https://www.langchain.com/langgraph)
  * Models: [OpenAI gpt-4o + gpt-4o-mini](https://platform.openai.com/docs/models)

## Process the datasets

* All processing was performed via a custom [Nextflow](https://www.nextflow.io/docs/latest/index.html) pipeline.
  * The pipeline was run on GCP Cloud Run.
  * Pipeline jobs in each run were processed via GCP Batch.
* Workflow:
  * Download a subset of reads via [fastq-dump](https://github.com/ncbi/sra-tools/wiki/HowTo:-fasterq-dump)
  * Use the subset to determine the best STAR parameters for the full alignment
    * e.g., cell barcodes and strand
  * Download all reads via [fasterq-dump](https://github.com/ncbi/sra-tools/wiki/HowTo:-fasterq-dump)
  * Align all reads with [STARsolo](https://github.com/alexdobin/STAR/blob/master/docs/STARsolo.md)
* Results:
  * STARsolo output (e.g., count matrices, gene-barcode matrices, etc.)

## Storing the results

* Dataset metadata and data processing information was stored in a GCP Cloud SQL database.
* STARsolo output was stored in GCP 

# Resources

* [Arc Institute](https://arcinstitute.org/)
* [scanpy](https://scanpy.readthedocs.io/en/stable/)
* [anndata](https://anndata.readthedocs.io/en/latest/)
* [pandas](https://pandas.pydata.org/docs/)

# Contact

* [GitHub Issues](https://github.com/ArcInstitute/arc-virtual-cell-atlas/issues)