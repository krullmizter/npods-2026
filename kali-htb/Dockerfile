FROM kalilinux/kali-rolling

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y --no-install-recommends \
        kali-linux-core \
        procps \
        psmisc \
        tmux \
        openvpn \
        iproute2 \
        iputils-ping \
        net-tools \
        telnet \
        ftp \
        openssh-client \
        smbclient \
        nmap \
        dnsutils \
        ffuf \
        gobuster \
        curl \
        wget \
        git \
        nano \
        vim \
        unzip \
        jq \
        python3 \
        python3-pip \
        john \
        wordlists \
        bash \
        ca-certificates && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

RUN gzip -d /usr/share/wordlists/rockyou.txt.gz || true

WORKDIR /root

CMD ["/bin/bash"]