# hash:sha256:fb1e01f00aef522cc47c9e68ba3177c87359e541bc8da97c8e6067da220236f6
FROM registry.acmecorp.codeocean.com/codeocean/jupyterlab:2.1.1-miniconda4.8.2-python3.8-ubuntu18.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y --no-install-recommends software-properties-common \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys \
        0x9FD3B784BC1C6FC31A8A0A1C1655A0AB68576280 \
        0xAD2323F17326AE31401037733E05EBFF05441C52 \
        E298A3A825C0D65DFD57CBB651716619E084DAB9 \
    && add-apt-repository -y 'deb http://deb.codeocean.com/rstudio-server-bionic/ ubuntu main' \
    && add-apt-repository -y 'deb http://deb.codeocean.com/shiny-server-trusty/ ubuntu main' \
    && add-apt-repository -y 'deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/' \
    && add-apt-repository -y 'deb https://deb.nodesource.com/node_12.x bionic main' \
    && apt-get purge -y --autoremove software-properties-common \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential=12.4ubuntu1 \
        gdebi-core=0.9.5.7+nmu2 \
        libgit2-dev=0.26.0+dfsg.1-1.1ubuntu0.2 \
        libssl-dev=1.1.1-1ubuntu2.1~18.04.6 \
        pkg-config=0.29.1-0ubuntu2 \
        r-base=3.6.3-1bionic \
        rstudio-server=1.2.5033 \
    && rm -rf /var/lib/apt/lists/*

RUN conda install -y \
        rstudio==1.1.456 \
    && conda clean -ya

RUN pip install -U --no-cache-dir \
    jupyter-rsession-proxy==1.2 \
    jupyter-server-proxy==1.5.0

COPY postInstall /
RUN /postInstall
