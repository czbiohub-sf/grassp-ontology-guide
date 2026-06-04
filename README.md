# Grassp Ontology Guide

> [!NOTE]
> **This is a fork of [chanzuckerberg/cellxgene-ontology-guide](https://github.com/chanzuckerberg/cellxgene-ontology-guide).**
> It extends the original to support non-animal species (e.g. yeast). All credit for the original work goes to the
> [Chan Zuckerberg Initiative](https://chanzuckerberg.com/) and the upstream contributors. 

CellxGene Ontology Guide is a filtered and curated collection of ontological metadata from different public sources.
The primary goal is to serve the ontology needs of the [CellxGene](https://cellxgene.cziscience.com/) project and its
associated tools. An [API](./api/python) for querying the data is also provided.

# Components

## Ontology Assets

The [ontology-assets](./ontology-assets) directory contains static ontology assets that are used by CellxGene
project. The jsonschema for these assets are stored in [asset-schemas](./asset-schemas).

This is a description of the files within the [ontology-assets](./ontology-assets) directory:

- [ontology_info.json](./ontology-assets/ontology_info.json) contains the ontology versions used by the current and deprecated [cellxgene-schema](https://github.com/chanzuckerberg/single-cell-curation/tree/main/schema)
- The `*.json.gz` files are filtered version of ontology sources found in [ontology_info.json](./ontology-assets/ontology_info.json). They are generated using the GHA workflow [generate_all_ontology.yml](.github/workflows/generate_all_ontology.yml) and the [all_ontology_generator.py](./tools/ontology-builder/src/all_ontology_generator.py) script.
- The `*_list.json` files are manually curated and are used to filter the ontologies.
- The `*_descendants.json` are descendant mapping files. They are generated on a weekly bases using the GHA workflow [generate_descendant_mappings.yml](./.github/workflows/generate_descendant_mappings.yml) and the [generate_descendant_mappings.py](./scripts/generate_descendant_mappings.py) script.

### Deprecating Ontologies

Older version of cellxgene-schema will be fully deprecated after 6 months of the release of a new version.

[TODO: document the process for deprecating ontologies](https://github.com/chanzuckerberg/cellxgene-ontology-guide/issues/170)

## Updating to a new Cellxgene Schema Version

1. Update the [ontology_info.json](./ontology-assets/ontology_info.json) file with the new schema version
2. Leave the older versions in the file for backward compatibility. They will be deprecated and removed automatically after 6 months. That process is handled in [deprecate_previous_cellxgene_schema_versions](https://github.com/chanzuckerberg/cellxgene-ontology/blob/main/tools/ontology-builder/src/all_ontology_generator.py#L311-L311).

# Maintainance
This repository is maintained by the [Computational Biology Platform](https://www.czbiohub.org/comp-biology/) at the [Chan Zuckerberg Biohub San Francisco](https://www.czbiohub.org/sf/)
