FROM jfloff/alpine-python:recent
LABEL maintainer="jfloff@inesc-id.pt"

RUN set -ex ;\
    echo "@community http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories ;\
    echo "@testing http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories ;\
    apk add --update --no-cache \
            # for matplotlib
            freetype-dev \
            tini@community \
            #for seaborn
            gfortran \
            openblas-dev@community \
            # for lxml
            libxslt-dev \
            py-lxml\
            ;\
    rm /var/cache/apk/*

RUN pip install --upgrade numpy \
                          scipy \
                          pandas \
                          matplotlib \
                          seaborn \
                          jupyter \
                          lxml \
                          ;\
    pip install --upgrade scikit-learn \
                          ;

# setup jupyter
EXPOSE 8888
ENV JUPYTER_PATH=/home/jupyter
RUN set -ex ;\
    jupyter notebook --generate-config --allow-root ;\
    sed -i -e "s/#c.NotebookApp.ip .*/c.NotebookApp.ip = '0.0.0.0'/g"  /root/.jupyter/jupyter_notebook_config.py ;\
    sed -i -e "s/#c.NotebookApp.port .*/c.NotebookApp.port = $JUPYTER_PORT/g"  /root/.jupyter/jupyter_notebook_config.py ;\
    sed -i -e "s/#c.NotebookApp.allow_root .*/c.NotebookApp.allow_root = True/g"  /root/.jupyter/jupyter_notebook_config.py

# for jupyter
ENTRYPOINT ["/sbin/tini", "--"]