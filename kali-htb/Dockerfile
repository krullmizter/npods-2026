FROM kalilinux/kali-rolling

ENV DEBIAN_FRONTEND=noninteractive \
    TERM=xterm-256color

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        kali-linux-core \
        # Networking & Protocol clients
        iproute2 iputils-ping net-tools dnsutils netcat-openbsd \
        telnet ftp openssh-client smbclient openvpn \
        # Recon & Web
        nmap ffuf gobuster dirb whatweb nikto sqlmap amass \
        # Cracking
        hydra john wordlists \
        # Utilities & Runtimes
        bash coreutils ca-certificates curl wget git \
        nano vim unzip jq tree file rlwrap tmux \
        procps psmisc python3 python3-pip && \
    if [ -f /usr/share/wordlists/rockyou.txt.gz ]; then \
        gunzip /usr/share/wordlists/rockyou.txt.gz; \
    fi && \
    # Clean up
    apt-get autoremove -y && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /root

CMD ["/bin/bash"]