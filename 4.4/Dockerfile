FROM centos:7

LABEL maintainer="stourac.jan@gmail.com"

ENV MOLPROBITY_VERSION 4.4
ENV MOLPROBITY_DIR /opt/MolProbity

RUN \
    yum groupinstall -y "@Development Tools" && \
    yum install -y \
        php-cli \
        python \
        bzip2-devel \
        zlib-devel \
        libXt-devel \
        subversion \
        git

RUN \
    git clone https://github.com/rlabduke/MolProbity.git --branch molprobity_${MOLPROBITY_VERSION} --single-branch --depth 1 ${MOLPROBITY_DIR} && \
    cd ${MOLPROBITY_DIR} && \
    ./configure.sh

RUN \
    cp ${MOLPROBITY_DIR}/config/config.php.sample ${MOLPROBITY_DIR}/config/config.php && \
    ln -s prekin_64 ${MOLPROBITY_DIR}/bin/linux/prekin && \
    ln -s scrublines_64 ${MOLPROBITY_DIR}/bin/linux/scrublines && \
    mkdir -p ${MOLPROBITY_DIR}/public_html/data && \
    chmod 777 ${MOLPROBITY_DIR}/public_html/data

ENV PATH="${MOLPROBITY_DIR}/bin/linux:${MOLPROBITY_DIR}/bin:${PATH}"
