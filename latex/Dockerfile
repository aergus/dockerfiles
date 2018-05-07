FROM debian:testing

ARG USERNAME=latex
ARG USERHOME=/home/latex
ARG ID=1000

RUN adduser --home "$USERHOME" --uid $ID --gecos "LaTeX" --disabled-password "$USERNAME"

RUN apt-get update && apt-get install -y \
  wget \
  git \
  make \
  texlive-full \ 
  # Required for syntax highlighting using minted.
  python-pygments && \
  # Removing documentation packages *after* installing them is kind of hacky,
  # but it only adds some overhead while building the image.
  apt-get --purge remove -y .\*-doc$ && \
  # Remove more unnecessary stuff
  apt-get clean -y
