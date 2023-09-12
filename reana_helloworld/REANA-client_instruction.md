# Snakemake backend for RECAST using REANA cluster
"Hello World!" example running with [Reana client](https://github.com/reanahub/reana-client):

For running this "Hello World" example with Reana cluster you firstly need to copy the git repository:

```
$ git clone https://github.com/AndriiPovsten/Snakemake-backend-for-RECAST.git
```
and switch to the reana_helloworld directory
``` 
$ cd reana_helloworld/
```
Also you need to create a conda virtual environment using a reana-environment.yml
```
$  conda env create -n Snakemake-reana-helloworld-example -f reana-environment.yml
```
Then, you can activate your conda environment via:
```
$ conda activate Snakemake-reana-helloworld-example
```

And now you need to authorize to the REANA:
```
$ export REANA_SERVER_URL=https://reana.cern.ch
$ export REANA_ACCESS_TOKEN=YOUR_PERSONAL_TOKEN
```
Firstly, you need to validate the:
```
$ reana-client validate -f reana-snakemake.yaml --environments --pull
```
After succesful validation we can run our workflow (here we name it snakemake-helloworld):
```
$ reana-client run -w snakemake-helloworld -f reana-snakemake.yaml --skip-validation
```
Now you can check the status of your workflow (sometimes it might take some time):
```
$ reana-client status -w snakemake-helloworld
```
And check the created files:
```
$ reana-client ls -w snakemake-helloworld --filter name=results
```
Finally, you can visualise your workflow via:
```
$ reana-client download -w snakemake-helloworld 'report.html'
```
For running everything in the container we can do the following:

Firstly you need to create an image using a Dockerfile:
```
$ docker build -t snakemake-reana .
```
Then, run it:
```
$ docker run --it --rm snakemake-reana
```
Our conda environment is located in the conda-envs you can check it via "conda info --envs" 
```
$ cd conda-envs/
```
Finally, activate Snakemake-reana-hellworld-example conda environment:
```
$ conda activate Snakemake-reana-helloworld-example
```
