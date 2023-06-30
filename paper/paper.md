---
title: 'BioHackJP 2023 Report R3: linked data standardization with LLMs'
title_short: 'BioHackJP 2023 Plants'
tags:
  - Linked Data
  - Plant genome
  - Plant breeding
authors:
  - name: Cyril Pommier
    orcid: 0000-0002-9040-8733
    affiliation: 1, 2
  - name: Hiromi Kajiya-Kanegae
    orcid: 0000-0002-5719-7559
    affiliation: 3
  - name: Andrea Ghelfi
    orcid: 0000-0001-9617-3309
    affiliation: 4
affiliations:
  - name: Université Paris-Saclay, INRAE, URGI, 78026, Versailles, France.
    index: 1
  - name: Université Paris-Saclay, INRAE, BioinfOmics, Plant bioinformatics facility, 78026, Versailles, France.
    index: 2
  - name: Research Center for Agricultural Information Technology (NARO), Tokyo, 105-0003, Japan
    index: 3
  - name: National Institute of Genetics (NIG), Shizuoka, 411-8540, Japan.
    index: 4
date: 30 June 2023
cito-bibliography: paper.bib
event: BH23JP
biohackathon_name: "BioHackathon Japan 2023"
biohackathon_url:   "https://2023.biohackathon.org/"
biohackathon_location: "Kagawa, Japan, 2023"
group: R3
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/biohackathon-japan/bh23-plant
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: Ghelfi A., Kajiya-Kanegae H, Pommier C.
---

# Background

The field of plant research is characterized by vast amounts of data generated from diverse sources and studies, resulting in significant data dispersion and heterogeneity. Researchers often face challenges in accessing, integrating, and analyzing these disparate datasets due to their low findability and to differences in formats, structures, and standards. Their are several solutions to this problem that cope with different parts of the FAIR principles. The plant community has decided in particular to solve the interoperability and the findability problem by building common data standards such as the Minimum Information About Plant Phenotyping Experiments (MIAPPE, www.miappe.org) and the Breeding API (BrAPI, www.brapi.org) as well as a data portal, FAIR Data-finder for Agronomic Research (FAIDARE). The building in those solutions has been initiated around 2015 with a global perspective in mind in the frame of european infrastructures (ELIXIR, EMPHASIS) and international networks(Bioversity of the CGIAR, NAPPN). The BioHackathon Japan 2023, was an ideal event to outreach those solutions toward the Japanese researchers and bioinformaticians in order to increase visibility of Japanese databases in the plant research data discovery portal FAIDARE and explore the use of the Breeding API for knowledge graph. 

The FAIDARE data portal has been initiated in 2015 in the frame of the ELIXIR European research infrastructure and the wheatIS of the wheat initiative (https://urgi.versailles.inrae.fr/faidare/ , http://www.wheatis.org/Search.php). It indexes 30 databases across the globe, including genomic, genetic and phenomic data. It provides search capabilities using full text approaches based on Elasticsearch, as well as ontology driven filters tailored for the need of plant researchers.  One of the keys to its success is its community management that eases the indexation of new databases (https://urgi.versailles.inrae.fr/faidare/join). Indeed, this indexation relies on (i) a minimal approach (Data discovery files) that allows to index any datatype or (ii) a more detailed one, based on the Breeding API specifications for genetic material (germplasm) and phenotyping or genotyping studies. 

The MIAPPE data standard is intialy designed to describe and formalize plant phenomics studies. But some of its elements are important shared key resources, or interoperability pivot. It is in particular the case of the plant genetic resources, or biological material. As a consequence, the Biological section of MIAPPE has been embeded in a dedicated [checklist](https://www.ebi.ac.uk/biosamples/schemas/certification/plant-miappe.json), used during EBI Biosample submission. Its usage has been documented in the Research Data Management Toolkit RDMKit and the FAIRCookBook. The [RDMKit](https://rdmkit.elixir-europe.org/) is a portal to best practices and guidelines that help researchers, data steward, producer and scientist to make their data FAIR (Findable, Accessible, Interoperable and Reusable). It contains a community maintained [plant page](https://rdmkit.elixir-europe.org/plant_sciences) that should be used as an entry point for plant data management. Furthermore, it links to a [Phenomic tools assembly](https://rdmkit.elixir-europe.org/plant_phenomics_assembly) and to a [Genomic tool assembly](https://rdmkit.elixir-europe.org/plant_genomics_assembly) which describe in details the submission workflow of genomic and variation data at EBI ENA and EVA.

We also identified an interesting opportunity around pedigrees and graph databases. Indeed several data resources around the globe propose pedigree informations such as Pedigree Finder[@Kajiya-Kanegae2022], [UK wheat varieties pedigree](https://www.niab.com/uk-wheat-varieties-pedigree), FAIDARE, CTPS or Eurisco in format such as the [Helium data format](https://github.com/cardinalb/helium-docs/wiki/Download-Helium) or BrAPI. 



# Outcomes

The main goal is to integrate germoplasm and genomic data in Japan at FAIDARE. Therefore, a mapping has been performed between BioSample database at DDBJ with MIAPPE specifications based on RDMkit. Mostly the attributes exist in both systems, with a different term (Table 1) and we are proposing to create a consensus MixS Plant extended accordingly with the Genomic Standards Consortioum ([GSC](http://www.gensc.org/pages/standards/checklists.html)) [checklists](http://www.gensc.org/pages/standards/checklists.html). We are proposing to create new fields at the DDBJ BioSample package in order to follow MIAPPE such as, biological material (latitute, longitude, altitude, coordinates uncertainty and preprocessing) and material source (ID, DOI, description, latitute, longitude, altitude, coordinates uncertainty). Some changes at DDBJ BioSample were suggested, the feature organism be split into genus and species, and unify strain, isolate, breed and cultivar as infraspecific name. Note that Biosample DDBJ packages are equivalent to EBI Checklists. 

We started the integration using a rice cultivar sample extrated from NARO, and BioSample ids were aggregated using taxon id and cultivar name. Using BioSample id, the experiments, study name and DDBJ URL were integrated with NARO dataset, such as Rice Core Collection of Japanese Landraces, [NARO Genebank](https://www.gene.affrc.go.jp/databases-core_collections_jr_en.php). 

Since BrAPI has Biosample ids the integration could be performed using the generated germoplasm and study datasets in json format, which were further indexed at FAIDARE.


Localhost, ready for FAIDARE beta then production


We reviewed the potential datasets, including aditional datasources to provide linked IDs between DDBJ Biosample, NARO, [Plant GARDEN](https://plantgarden.jp/en/index) at Kazusa DNA Research Institute. Nonetheless, a more exhaustive review of the data and linked ID resources is necessary before carrying on that work. 




![Caption for BioHackrXiv logo figure](./biohackrxiv.png)

# Future work



## Acknowledgements

We would like to thank the fellow participants at BioHackathon 2023 for their collaboration and constructive advice, which greatly influenced our project. We are grateful to the organizers for providing this platform. Special thanks to our mentors, advisors, and colleagues for their guidance and support. Without their contributions, our project in linked data standardization would not have been possible.

## References

1.

## Annexes 



**Table:Mapping DDBJ Biosample plant to ENA Plant MIAPPE Checklist**
https://github.com/ddbj/pub/tree/master/docs/biosample
https://www.ebi.ac.uk/biosamples/schemas/certification/plant-miappe.json

|Field from DDBJ corresponding to the checklist|DDBJ Biosample Plants <br>DDBJ new package Field Name|ENA Plant MIAPPE Checklist <br>Field name|ENA Plant MIAPPE Checklist <br>comment|ENA Plant MIAPPE Checklist <br>Cardinality|ENA Plant MIAPPE Checklist <br>source|
|------|------|------|------|------|------|
||bioproject_id|project name|Introduce the notion of investigation ? A project can have several investigation|optional|Gsc MIxS|
||sample_name|(DM-41) Biological material ID||mandatory|MIAPPE|
||taxonomy_id|(DM-42) Organism||mandatory|MIAPPE|
|organism|genus|(DM-43) Genus||optional|MIAPPE|
||species|(DM-44) Species||optional|MIAPPE|
|strain, isolate, breed, cultivar|infraspecific_name|(DM-44') Infraspecific name||recommended|MIAPPE|
||ecotype|ecotype||optional|ENA Plant|
||biological_material_latitute|(DM-45) Biological material latitude||optional|MIAPPE|
||biological_material_longitude|(DM-46) Biological material longitude||optional|MIAPPE|
||biological_material_altitude|(DM-47) Biological material altitude||optional|MIAPPE|
||biological_material_coordinates_uncertainty|(DM-48) Biological material coordinates uncertainty||optional|MIAPPE|
||geo_loc_name|Biological material geographic location (country and/or sea)|To be discussed|optional|MIAPPE|
||biological_material_preprocessing|(DM-49) Biological material preprocessing||optional|MIAPPE|
||material_source_ID|(DM-50) Material source ID (Holding institute/stock centre, accession)||recommended|MIAPPE|
||material_source_DOI|(DM-51) Material source DOI||recommended|MIAPPE|
||material_source_latitute|(DM-52) Material source latitude||optional|MIAPPE|
||material_source_longitude|(DM-53) Material source longitude||optional|MIAPPE|
||material_source_altitude|(DM-54) Material source altitude||optional|MIAPPE|
||material_souce_coordinates_uncertainty|(DM-55) Material source coordinates uncertainty||optional|MIAPPE|
||material_source_description|(DM-56) Material source description||optional|MIAPPE|
||Material source geographic location|Material source geographic location (country and/or sea)|To be discussed|optional|MIAPPE|
||ploidy|Biological material ploidy|should us ethe existing "ploidy" field instead|recommended|ENA Plant|
||collected_by|collected_by||optional|ENA Plant|
||collection_date|collection date||optional|ENA Plant, MIAPPE DM-80|
||sex|sex||optional|ENA Crop Plant|
||env_broad_scale|environment (biome)||optional|ENA Plant|
||dev_stage|DM-77 Plant structure development
stage||optional|MIAPPE|
||host_anatomical_material|DM-78 Plant anatomical entity||optional|MIAPPE|
||description|DM-79 Sample description|Or replace with the many fields taken from ENA Plant Sample|recommended|MIAPPE|
||sample_id|DM-75 Sample ID|List of IDs, different from BiosampleID, used for interoperability and for linking sample within different datafiles|recommended|MIAPPE/ENA|
||env_parameter|Environment parameter|Environment parameter = Environment parameter value|optional|MIAPPE|
||Material Source Institute code|DM-xx95 Material Source Institute code|FAO WIEWS code of the institute where the accession is maintained. The codes consist of the 3-letter ISO 3166 country code of the country where the institute is located plus a number (e.g. COL001). The current set of institute codes is available from http://www.fao.org/wiews. For those institutes not yet having an FAO Code, or for those with ‘obsolete’ codes, see ‘Common formatting rules (v)’. If no Institue code, create your own (Laboratory accronyme, Research Institute Acronyme, ...).|||
||Material Source Accession number|DM-xx96 Material Source Accession number|This is the unique identifier for accessions within a genebank, and is assigned when a sample is entered into the genebank collection (e.g. ‘PI 113869’). If not a genebank, use a laboratory ID. In the case of a commercial Variety, use the variety anme or code.|||
