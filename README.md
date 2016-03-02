# Differential expression signatures for disease using STARGEO

[STARGEO](http://stargeo.org/) is a webapp which allows users to identify differentially expressed genes between samples of their choosing. Users annotate studies in [GEO](http://www.ncbi.nlm.nih.gov/geo/ "Gene Expression Omnibus") to indicate which samples belong to which conditions. We've annotated many samples for their membership to specific disease or control classes. Then for a specific query (case versus control specification), STARGEO meta-analyzes across all the studies with relevant samples.

Here, we perform STARGEO analyses for diseases in our drug repurposing hetnet. See the [_Thinklab_ discussion](https://doi.org/10.15363/thinklab.d96) for more information.

## Execution

This repository depends on the [`starapi`](https://github.com/idrdex/star_api) package. See `environment.yml` for the other installed packages in the environment.

The notebooks are executed in the following order:

1. [`retrieve-tags.ipynb`](retrieve-tags.ipynb) retrieves the current tags from the STARGEO database. The connection details are stored in `dsn.txt` (private).
2. [`prepare_queries.ipynb`](prepare_queries.ipynb) prepares the STARGEO queries based off of manual Disease Ontology to STARGEO tag mappings ([`data/DO-tag-mapping.tsv`](data/DO-tag-mapping.tsv)). The queries specifics are stored in [`data/queries.tsv`](data/queries.tsv).
3. [`querier.ipynb`](querier.ipynb) performs the STARGEO analyses. The output for each disease is stored in [`data/doslim`](data/doslim).
4. [`combine.ipynb`](combine.ipynb) aggregates the differential expression results for all diseases. [`data/diffex.tsv`](data/diffex.tsv) contains the significantly differential expressions. [`data/summary.tsv`](data/summary.tsv) shows the number of up and down-regulated genes per disease.

## License

All original content in this repository is released under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/ "Creative Commons · Public Domain Dedication").
