FROM condaforge/mambaforge:latest
LABEL io.github.snakemake.containerized="true"
LABEL io.github.snakemake.conda_env_hash="a27eb1bd907da7d709dcbe093527f3ae2ce3ac8b4a9f4ec63cc1a34b4e1f4dc0"

# Step 1: Retrieve conda environments

# Conda environment:
#   source: reana-environment.yml
#   prefix: /conda-envs/91337d203b301eff9917a563c6a59592
#   name: Snakemake-reana-helloworld-example
#   channels:
#     - conda-forge
#   dependencies:
#     - python=3.10
#     - bioconda::snakemake=7.25.0
#     - pip
#     - pytest
#     - pandas
#     - samtools
#     - matplotlib
#     - ruff
#     - pip:
#       - reana-client
RUN mkdir -p /conda-envs/91337d203b301eff9917a563c6a59592
COPY reana-environment.yml /conda-envs/91337d203b301eff9917a563c6a59592/environment.yaml

# Step 2: Generate conda environments

RUN mamba env create --prefix /conda-envs/91337d203b301eff9917a563c6a59592 --file /conda-envs/91337d203b301eff9917a563c6a59592/environment.yaml && \
    mamba clean --all -y
