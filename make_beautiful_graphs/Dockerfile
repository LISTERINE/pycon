FROM listerine/dev-env
MAINTAINER Jonathan Ferretti

WORKDIR /

RUN apt-get update && apt-get install -y wget bzip2 ca-certificates \
    libglib2.0-0 libxext6 libsm6 libxrender1
RUN echo 'export PATH=/opt/conda/bin:$PATH' > /etc/profile.d/conda.sh && \
    wget --quiet https://repo.continuum.io/archive/Anaconda3-2.3.0-Linux-x86_64.sh && \
    /bin/bash /Anaconda3-2.3.0-Linux-x86_64.sh -b -p /opt/conda && \
    rm /Anaconda3-2.3.0-Linux-x86_64.sh && \
    /opt/conda/bin/conda install --yes conda==3.14.1

ENV PATH /opt/conda/bin:$PATH

RUN git clone https://github.com/plotly/pycon-2015.git

WORKDIR pycon-2015

RUN /bin/bash -c "conda run ipython profile create nbserver"

# Inject notebook settings
RUN printf "%s\n" "c.IPKernelApp.pylab = 'inline'" >> /root/.ipython/profile_nbserver/ipython_notebook_config.py && \
	printf "%s\n" "c.NotebookApp.ip = '*'" >> /root/.ipython/profile_nbserver/ipython_notebook_config.py && \
	printf "%s\n" "c.NotebookApp.open_browser = False" >> /root/.ipython/profile_nbserver/ipython_notebook_config.py && \
	printf "%s\n" "c.NotebookApp.port = 80" >> /root/.ipython/profile_nbserver/ipython_notebook_config.py

RUN /bin/bash -c "pip install plotly"

CMD ["/bin/bash", "-c", "conda run 'ipython notebook --profile=nbserver'"]
