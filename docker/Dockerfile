# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=jupyter/pyspark-notebook:76402a27fd13
FROM $BASE_CONTAINER

LABEL maintainer="Hanbin Seo <hanbin.seo@meshkorea.net>"

RUN pip install sparkmagic --quiet && \
    jupyter nbextension enable --py --sys-prefix widgetsnbextension && \
    jupyter labextension install "@jupyter-widgets/jupyterlab-manager"

USER root
RUN cd /opt/conda/lib/python3.7/site-packages && \
    jupyter-kernelspec install sparkmagic/kernels/pysparkkernel && \
    jupyter serverextension enable --py sparkmagic

USER $NB_UID
WORKDIR $HOME
