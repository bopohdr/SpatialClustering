# SpatialClustering #

An implementation to the spatial clustering algorithm to calculate clustering of variants over cDNA.
This algorithm was featured in the publication "Spatial Clustering of De Novo Missense Mutations Identifies Candidate Neurodevelopmental Disorder-Associated Genes"

## Citation ##

If you make use of this software for academic purposes, please cite the article [10.1016/j.ajhg.2017.08.004](https://doi.org/10.1016/j.ajhg.2017.08.004).

## How to run ##

### Dependencies ###

The code implemented here is tested in a Python 3.5.x environment and should work for Python 2.7.x.
To install the virtual environment, please follow the following steps:

    pip3 install virtualenv
    After cloning this repository, ensure that you are in the project's directory. 
    
Create virtual environment for the project

    Python 2.7.x: > mkvirtualenv --no-site-packages SpatialClustering_env
    Python 3.8.x: > virtualenv SpatialClustering_env

Activate virtual environment for installing packages

    Python 2.7.x: > workon SpatialClustering_env
    Python 3.8.x: > source SpatialClustering_env/bin/activate

Install required packages for current project

    Python 2.7.x: > pip install -r requirements.txt
    Python 3.8.x: > pip install -r requirements.txt

Exit the virtual environment

    Python 2.7.x: > deactivate
    Python 3.8.x: > deactivate

All dependencies should now be installed in the virtual environment.

### Example run ###

Exampe for a hypothetical gene

    Python 2.7.x: > workon SpatialClustering_env
    Python 2.7.x: (SpatialClustering_env) > python spatial_clustering/spatial_clustering.py --gene_name=TESTGENE --variant_cDNA_locations=1,2,3,4,5,5,5,10,1000 --cDNA_length=1337 --n_permutations=10 --parallel=True --random_seed=1 --correction=1
    Python 2.7.x: (SpatialClustering_env) > deactivate
    ~
    Python 3.5.x: >  SpatialClustering_env/bin/python spatial_clustering/spatial_clustering.py --gene_name=TESTGENE --variant_cDNA_locations=1,2,3,4,5,5,5,10,1000 --cDNA_length=1337 --n_permutations=10 --parallel=True --random_seed=1 --correction=1

This should result in the following output:
    
    Computing spatial clustering for gene: TESTGENE
    cDNA_length: 1337
    variant_cDNA_locations: ['1', '2', '3', '4', '5', '5', '5', '10', '1000']
    Settings: random_seed: 1, parallel: True, n_permutations: 10

    Results:
    gene: TESTGENE, with n variants: 9
    geometric_mean: 6.898887607777424e-08
    corrected p-value: 0.09090909090909091 (Bonferroni correction = 1)

The arguments '--n_permutations', '--parallel', `--random_seed`, and, `--correction` are optional and need nit be included.

For further information on arguments, please refer to the help file:

    -h, --help            show this help message and exit
    --gene_name GENE_NAME
                          (Required) Name of the gene of interest, example
                          usage: --gene_name=BRCA1
    --variant_cDNA_locations VARIANT_CDNA_LOCATIONS
                          (Required) cDNA based variant locations, example
                          usage: --variant_cDNA_locations=10,50,50,123
    --cDNA_length CDNA_LENGTH
                          (Required) total cDNA length of the gene (including
                          stop codon), example usage: --cDNA_length=1337
    --n_permutations N_PERMUTATIONS
                          (Optional) total nunber of permutations,
                          default=100000000 (1.00E+08), example usage:
                          --n_permutations=100
    --parallel PARALLEL   (Optional) should the algorithm make use of parallel
                          computation?, default=True, example usage:
                          --parallel=True
    --random_seed RANDOM_SEED
                          (Optional) The seed used for initialization of the
                          random permutations, default=1, example usage:
                          --random_seed=1
    --correction CORRECTION
                          (Optional) The number of genes the p-value must be
                          corrected for in a Bonferonni manner, default=1,
                          example usage: --correction=1
