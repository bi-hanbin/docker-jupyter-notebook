# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=jupyter/pyspark-notebook:76402a27fd13
FROM $BASE_CONTAINER

LABEL maintainer="Hanbin Seo <hanbin.seo@meshkorea.net>"

RUN pip install sparkmagic && \
    jupyter nbextension enable --py --sys-prefix widgetsnbextension && \
    jupyter labextension install "@jupyter-widgets/jupyterlab-manager"

USER root

RUN cd /opt/conda/lib/python3.7/site-packages && \
    jupyter-kernelspec install sparkmagic/kernels/pysparkkernel && \
    jupyter serverextension enable --py sparkmagic && \
    mkdir $HOME/.sparkmagic

COPY sparkmagic/config.json $HOME/.sparkmagic

RUN chown -R jovyan:users $HOME/.sparkmagic && \
    chown -R jovyan:users $HOME/.local

USER $NB_UID

WORKDIR $HOME
