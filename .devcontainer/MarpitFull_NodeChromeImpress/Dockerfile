FROM library/node:lts-bookworm

ARG DEBIAN_FRONTEND=noninteractive
RUN apt update \
    && apt install -y --no-install-recommends sudo \
    && apt autoremove -y \
    && rm -rf /var/lib/apt/lists/* \
    && echo "node ALL=(ALL) NOPASSWD: ALL" >/etc/sudoers.d/node \
    && chmod 0440 /etc/sudoers.d/node

# Install LibreOffice Impress
RUN apt-get update && \
    apt-get install -y --no-install-recommends libreoffice-impress && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install Google Chrome browser
RUN apt-get update && \
    apt-get install -y --no-install-recommends wget gnupg && \
    wget -O /tmp/google-chrome.deb https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb && \
    apt-get install -y --no-install-recommends /tmp/google-chrome.deb && \
    rm /tmp/google-chrome.deb && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install code-server (VS Code in browser) and Marp extension
RUN curl -fsSL https://code-server.dev/install.sh | sh
RUN code-server --install-extension marp-team.marp-vscode --force
