# hash:sha256:d1c73b849290675ccae29ae59350b751d213ad38fa47b75492241aa3b1f41f7e
FROM registry.acmecorp.codeocean.com/codeocean/jupyterlab:2.1.1-miniconda4.8.2-python3.8-ubuntu18.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y --no-install-recommends software-properties-common \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys \
        E298A3A825C0D65DFD57CBB651716619E084DAB9 \
    && add-apt-repository -y 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/' \
    && apt-get purge -y --autoremove software-properties-common \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential=12.4ubuntu1 \
        gdebi-core=0.9.5.7+nmu2 \
        libgit2-dev=0.26.0+dfsg.1-1.1ubuntu0.2 \
        libssl-dev=1.1.1-1ubuntu2.1~18.04.6 \
        pkg-config=0.29.1-0ubuntu2 \
        r-base=3.6.3-1bionic \
    && rm -rf /var/lib/apt/lists/*

RUN conda install -y \
        rstudio==1.1.456 \
    && conda clean -ya

RUN pip install -U --no-cache-dir \
    jupyter-rsession-proxy==1.2
