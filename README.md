# Snakemake backend for RECAST
This is a small "Hello World!" example which will give you a brief understanding of [Snakemake](https://snakemake.readthedocs.io/en/stable/) and [Conda](https://docs.conda.io/en/latest/) usage.

For running this Hello World example you firstly need to copy the git repository:
<pre>
```
$ git clone https://github.com/AndriiPovsten/Snakemake-backend-for-RECAST.git
```
and switch to the recast_helloworld directory
``` 
$ cd recast_helloworld/

$  conda env create -n Snakemake-example-hello-world -f environment.yml
```
Then, you can activate your conda environment via:
``` bash
$ conda activate Snakemake-example-hello-world
```
Now, you can execute the Snakemake workflow:
``` 
$ snakemake --cores 1 --use-conda --conda-cleanup-pkgs cache   
```
Alternitavely you can specify the directory and Snakefile explicitly:
``` 
$ snakemake --directory recast_helloworld/ --snakefile recast_helloworld/Snakefile --cores 1 --use-conda --conda-cleanup-pkgs cache
```
If you prefer to run this workflow within a Docker container you can follow this steps:
Creating a Docker image using the 'mambaorg/micromamba' image
``` 
$ docker run --rm -ti -v $PWD:/work:ro mambaorg/micromamba:1.4.9-bullseye-slim 
```
Create a new environment and activate it:
``` 
(base) mambauser@b34a3dfcc306:/tmp$ micromamba create --yes --file /work/environment.yml
(base) mambauser@b34a3dfcc306:/tmp$ micromamba activate Snakemake-example-hello-world
</pre>
```