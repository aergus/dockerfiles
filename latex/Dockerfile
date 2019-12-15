FROM debian:testing

ARG USER_NAME=latex
ARG USER_HOME=/home/latex
ARG USER_ID=1000
ARG USER_GECOS=LaTeX

RUN adduser \
  --home "$USER_HOME" \
  --uid $USER_ID \
  --gecos "$USER_GECOS" \
  --disabled-password \
  "$USER_NAME"

ARG WGET=wget
ARG GIT=git
ARG MAKE=make
ARG PANDOC=pandoc
ARG PCITEPROC=pandoc-citeproc
ARG PYGMENTS=python3-pygments
ARG MATPLOTLIB=python3-matplotlib
ARG SCIPY=python3-scipy
ARG SYMPY=python3-sympy
ARG FIG2DEV=fig2dev
ARG JRE=default-jre-headless

RUN apt-get update && apt-get install -y \
  texlive-full \
  # some auxiliary tools
  "$WGET" \
  "$GIT" \
  "$MAKE" \
  # markup format conversion tool
  "$PANDOC" \
  "$PCITEPROC" \
  # XFig utilities
  "$FIG2DEV" \
  # syntax highlighting package
  "$PYGMENTS" \
  # scientific packages for pythontex usage
  "$MATPLOTLIB" \
  "$SCIPY" \
  "$SYMPY" \
  # Java runtime environment (e.g. for arara)
  "$JRE" && \
  # Removing documentation packages *after* installing them is kind of hacky,
  # but it only adds some overhead while building the image.
  apt-get --purge remove -y .\*-doc$ && \
  # Remove more unnecessary stuff
  apt-get clean -y
