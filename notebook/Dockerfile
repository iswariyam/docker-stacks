FROM digiklausur/minimal-notebook:latest

LABEL maintainer="DigiKlausur project HBRS <mohammad.wasil@h-brs.de>"

USER $NB_USER

COPY requirements.txt /tmp/requirements.txt

RUN pip install --no-cache-dir -r /tmp/requirements.txt

RUN pip install --no-cache-dir jupyterhub==1.1.*

RUN jupyter nbextension enable --py widgetsnbextension --sys-prefix && \
    jupyter serverextension enable --py jupyterlab --sys-prefix

# Install nbzip
RUN pip install --no-cache-dir nbzip==0.1.0 && \
    jupyter serverextension enable  --sys-prefix --py nbzip && \
    jupyter nbextension     install --sys-prefix --py nbzip && \
    jupyter nbextension     enable  --sys-prefix --py nbzip

# Install RISE for presentation
RUN pip install --no-cache-dir RISE==5.6.1 && \
    jupyter-nbextension install rise --py --sys-prefix

# Install codefolding and google translate
RUN pip install --no-cache-dir jupyter-contrib-nbextensions==0.5.1 && \
    jupyter contrib nbextension install --sys-prefix && \
    jupyter nbextension enable --sys-prefix codefolding/main && \
    jupyter nbextension enable --sys-prefix nbTranslate/main && \
    jupyter nbextension enable --sys-prefix collapsible_headings/main

# Install drawio
#RUN jupyter labextension install jupyterlab-drawio

# Install jupyterlab-latex
#RUN pip install jupyterlab_latex==0.4.1 && \
#    jupyter labextension install @jupyterlab/latex

#Install nbgrader and H-BRS DigiKlausur nbextension
RUN pip install  --no-cache-dir git+http://git@github.com/DigiKlausur/nbgrader.git@v0.7.0-dev-k8s
RUN jupyter serverextension enable --sys-prefix --py nbgrader &&\
    jupyter nbextension install --sys-prefix --py nbgrader --overwrite &&\
    jupyter nbextension enable --sys-prefix assignment_list/main --section=tree &&\
    jupyter serverextension enable --sys-prefix nbgrader.server_extensions.assignment_list

RUN cd /tmp && \
    git clone https://github.com/DigiKlausur/Jupyter-Extensions.git && \
    cd /tmp/Jupyter-Extensions/nbextensions && \
    jupyter nbextension install assignment_view --sys-prefix && \
    jupyter nbextension enable assignment_view/main --sys-prefix

RUN jupyter nbextension list
