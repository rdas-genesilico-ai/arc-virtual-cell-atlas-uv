Arc Virtual Cell Atlas
======================

The Arc Virtual Cell Atlas is a collection of high quality, curated, open datasets assembled for the purpose of accelerating the creation of virtual cell models.
The atlas includes both observational and perturbational data from over 330 million cells (and growing).

The atlas is bootstrapped with [Vevo’s](https://www.vevo.ai/) Tahoe-100 and [Arc’s](https://arcinstitute.org/) AI agent-curated scBaseCamp dataset.

## IMPORTANT NOTICE

> We are converting file extensions from `parquet.gz` and `h5ad.gz` to `parquet` and `h5ad`, respectively. The `*.gz` files will be **deleted on Friday, Feb 26 2025 at 5:00 PM PST.**
You can copy just the `parquet` and `h5ad`, files via: `rsync`:

```bash
gsutil -m rsync -r -x "^(?\!.*\.parquet$)" "gs://arc-ctc-scbasecamp/2025-02-25/metadata"
```

```bash
gsutil -m rsync -r -x "^(?\!.*\.h5ad$)" "gs://arc-ctc-scbasecamp/2025-02-25/h5ad"
```

**Sorry for the inconvience!**



# Tahoe-100

[Documentation](./tahoe-100/README.md)

# scBaseCamp

[Documentation](./scBaseCamp/README.md)

