FROM quay.io/bedrock/ubuntu:xenial-20201030

RUN apt-get update -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    acl \
    apache2 \
    asciidoc \
    bzip2 \
    cdbs \
    curl \
    debhelper \
    debianutils \
    devscripts \
    docbook-xml \
    dpkg-dev \
    fakeroot \
    gawk \
    gcc \
    git \
    iproute2 \
    libffi-dev \
    libssl-dev \
    libxml2-utils \
    locales \
    lsb-release \
    make \
    openssh-client \
    openssh-server \
    python-cryptography \
    python-dev \
    pass \
    python-dbus \
    python-httplib2 \
    python-jinja2 \
    python-lxml \
    python-mock \
    python-nose \
    python-packaging \
    python-passlib \
    python-pip \
    python-setuptools \
    python-virtualenv \
    python-wheel \
    python-yaml \
    reprepro \
    rsync \
    ruby \
    sshpass \
    subversion \
    sudo \
    tzdata \
    unzip \
    virtualenv \
    xsltproc \
    zip \
    && \
    apt-get clean \
    && \
    rm -rf /var/lib/apt/lists/*

RUN rm /etc/apt/apt.conf.d/docker-clean
RUN mkdir /etc/ansible/
RUN /bin/echo -e "[local]\nlocalhost ansible_connection=local" > /etc/ansible/hosts
RUN locale-gen en_US.UTF-8
RUN ssh-keygen -m PEM -q -t rsa -N '' -f /root/.ssh/id_rsa && \
    cp /root/.ssh/id_rsa.pub /root/.ssh/authorized_keys && \
    for key in /etc/ssh/ssh_host_*_key.pub; do echo "localhost $(cat ${key})" >> /root/.ssh/known_hosts; done
VOLUME /sys/fs/cgroup /run/lock /run /tmp
RUN pip install 'coverage==4.5.4' 'resolvelib==0.5.4' 'junit-xml==1.9'
ENV container=docker
CMD ["/sbin/init"]
