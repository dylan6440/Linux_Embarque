# Based on Debian 9
FROM debian:latest as ynov-ctng-latest

# LABEL about the custom image
LABEL maintainer="dylan.orto@ynov.com" 
# Your Ynov Bordeaux Campus student email address
LABEL version="0.1" 
# First version, nothing to change!
LABEL description="Welcome" 
# Add a relevant description of the image here! (Recommended)

# Make the creation of docker images easier so that CTNG_UID/CTNG_GID have
# a default value if it's not explicitly specified when building. This
# will allow publishing of images on various package repositories (e.g.
# docker hub, gitlab containers). dmgr.sh can still be used to set the
# UID/GID to that of the current user when building a custom container.
ARG CTNG_UID=1000
ARG CTNG_GID=1000
# File to configure for your raspberry pi version
ARG CONFIG_FILE

# Crosstool-ng must be executed from a user that isn't the superuser (root)
# You must create a user and add it to the sudoer group
# Help : https://phoenixnap.com/kb/how-to-create-sudo-user-on-ubuntu
# https://phoenixnap.com/kb/how-to-create-sudo-user-on-ubuntu
# <CommandeS pour créer votre nouvel utilisateur et lui accorder les droits sudoer>
RUN useradd -ms /bin/bash userconfig \
&& usermod -aG sudo userconfig
# You will need to update the repository list before updating your system in order to install some of the packages
# Use the sources.list provided with the lab materials
# On ubuntu, lookup the command add-apt-repository and the repos universe and multiverse?
# RUN <Commands to add repo, if necessary??>

RUN apt-get -y update && apt-get -y upgrade 

# Install necessary packages to run crosstool-ng
# You don't remember the previous lectures on the crosstool-ng?
# Use google : install crosstool-ng <Your distribution>??
RUN apt-get install -y gcc-arm-linux-gnueabi build-essential git autoconf bison flex help2man gawk libtool-bin libncurses5-dev gperf bison flex texinfo unzip
# Install Dumb-init
# https://github.com/Yelp/dumb-init
RUN apt-get install -y dumb-init
RUN echo 'export PATH=/opt/ctng/bin:$PATH' >> /etc/profile
# ENTRYPOINT [ "/usr/local/bin/dumb-init", "--" ]

# Login with user 
USER userconfig
WORKDIR /home/userconfig
# Download and install the latest version of crosstool-ng
# https://github.com/crosstool-ng/crosstool-ng.git
RUN git clone -b master --single-branch --depth 1 \
    https://github.com/crosstool-ng/crosstool-ng.git ct-ng
WORKDIR /home/userconfig/ct-ng
# <commands to configure and install crosstool-ng>
RUN ./bootstrap \
&& ./configure --enable-local \
&& make

ENV PATH=/home/userconfig/.local/bin:$PATH
COPY ${CONFIG_FILE} config
# Build ct-ng
# <Build command(s)>
RUN ./configure --${CONFIG_FILE} \
&& make

ENV TOOLCHAIN_PATH=/home/dev/x-tools/${CONFIG_FILE}
ENV PATH=${TOOLCHAIN_PATH}/bin:$PATH

CMD ["bash"]
