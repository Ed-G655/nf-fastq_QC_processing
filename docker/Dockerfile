
################## BASE IMAGE ######################
FROM rocker/tidyverse
################## METADATA ######################
LABEL base_image="rocker/tidyverse"
LABEL version="0"
LABEL software="nf-fastq_QC_processing"
LABEL software.version="0.0.2"
LABEL about.summary="Nextflow pipeline to analyze and modify fastq sequence quality"
LABEL about.home="https://github.com/Iaguilaror/nf-fastq_QC_processing.git"
LABEL about.documentation="https://github.com/Iaguilaror/nf-fastq_QC_processing.git"
LABEL about.tags="Genomics"

################## MAINTAINER ######################
MAINTAINER Jose Eduardo Garcia Lopez <jeduardogl655@gmail.com>

################## INSTALLATION ######################

# install pipeline requirements
RUN apt-get update && apt-get install -y --no-install-recommends \
  default-jre \
  curl \
  pandoc \
  trimmomatic \
  fastqc \
  git

# install python3 and pip
RUN apt-get install -y --no-install-recommends \
      python3.5 \
      python3-pip \
      && apt-get clean && \
      rm -rf /var/lib/apt/lists/*

# install multiqc
RUN pip install multiqc

# install LATEX dependecies
RUN apt-get install -y --no-install-recommends \
  texlive-latex-base \
  texlive-fonts-recommended \
  texlive-fonts-extra \
  texlive-latex-extra \
  libfontconfig1-dev \
  texlive-plain-generic \
  lmodern

# install nextflow
#RUN curl -s https://get.nextflow.io | bash
#RUN chmod +x nextflow
#RUN mv nextflow bin/nextflow


# install R packages
RUN apt-get update -qq && apt-get -y --no-install-recommends install \
  && install2.r --error \
    vroom \
    cowplot \
    knitr

# install the kableExtra  and tinytex package using install.packages
RUN Rscript -e "install.packages('kableExtra')"
RUN Rscript -e "install.packages('tinytex')"

# install mk
RUN git clone https://github.com/9fans/plan9port.git
RUN cd plan9port && ./INSTALL
RUN  ln -s /plan9port/bin/mk /bin
