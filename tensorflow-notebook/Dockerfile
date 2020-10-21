# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
ARG BASE_CONTAINER=jupyter/scipy-notebook
FROM $BASE_CONTAINER

LABEL maintainer="Jupyter Project <jupyter@googlegroups.com>"


RUN conda install --quiet --yes \
'geopandas' 
RUN conda clean --all -f -y && \
    # Activate ipywidgets extension in the environment that runs the notebook server
    jupyter nbextension enable --py widgetsnbextension --sys-prefix && \
    # Also activate ipywidgets extension for JupyterLab
    # Check this URL for most recent compatibilities
    # https://github.com/jupyter-widgets/ipywidgets/tree/master/packages/jupyterlab-manager
    jupyter labextension install @jupyter-widgets/jupyterlab-manager@^2.0.0 --no-build && \
    jupyter labextension install @bokeh/jupyter_bokeh@^2.0.0 --no-build && \
    jupyter labextension install jupyter-matplotlib@^0.7.2 --no-build && \
    jupyter lab build -y && \
    jupyter lab clean -y && \
    npm cache clean --force && \
    rm -rf "/home/${NB_USER}/.cache/yarn" && \
    rm -rf "/home/${NB_USER}/.node-gyp" && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

RUN pip install --quiet --no-cache-dir \
    'requests' 
RUN pip install --quiet --no-cache-dir \
    'flask' 
RUN pip install --quiet --no-cache-dir \
    'streamlit' 
RUN pip install --quiet --no-cache-dir \
    'sweetviz' 

RUN pip install --quiet --no-cache-dir \
    'sidetable' 

RUN pip install --quiet --no-cache-dir \
    'bokeh' 

RUN pip install --quiet --no-cache-dir \
    'hiplot' 
RUN pip install --quiet --no-cache-dir \
    'xlsxwriter' 

RUN pip install --quiet --no-cache-dir \
    'tensorflow==2.3.0' \
     && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"
