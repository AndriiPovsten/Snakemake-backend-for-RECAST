FROM condaforge/mambaforge:latest
LABEL io.github.snakemake.containerized="true"
ARG conda_env_name=Snakemake-reana-helloworld-example

RUN mkdir -p /conda-envs/${conda_env_name}
COPY reana-environment.yml /conda-envs/${conda_env_name}/environment.yaml


RUN mamba env create --prefix /conda-envs/${conda_env_name} --file /conda-envs/${conda_env_name}/environment.yaml && \
    mamba clean --all -y
