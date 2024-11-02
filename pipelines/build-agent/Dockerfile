# Use the latest Ubuntu image as base
FROM ubuntu:latest

# Install dependencies and Docker
RUN apt-get update && apt-get install -y \
    ca-certificates \
    curl \
    gnupg \
    lsb-release && \
    mkdir -p /etc/apt/keyrings && \
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
    gpg --dearmor -o /etc/apt/keyrings/docker.gpg && \
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null && \
    apt-get update && \
    apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /home/ubuntu
RUN curl -O https://vstsagentpackage.azureedge.net/agent/3.246.0/vsts-agent-linux-x64-3.246.0.tar.gz
RUN tar zvxf vsts-agent-linux-x64-3.246.0.tar.gz
RUN ./bin/installdependencies.sh
RUN usermod -aG docker ubuntu && newgrp
# Enable Docker-in-Docker
#RUN dockerd &

# Expose Docker daemon port
EXPOSE 2375

RUN usermod -aG sudo ubuntu
RUN echo "ubuntu ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

RUN echo "#!/bin/bash" >> agentsetup.sh
RUN echo 'agent=$1' >> agentsetup.sh
RUN chmod +x agentsetup.sh
RUN echo './config.sh --unattended --url https://dev.azure.com/$ORG --auth pat --token $token --pool $pool --agent $agent --work _work --replace --acceptTeeEula' >> agentsetup.sh
RUN echo './run.sh &' >> agentsetup.sh

# Set entrypoint to run Docker daemon in the background and keep container alive
CMD ["sh", "-c", "dockerd & tail -f /dev/null"]

# Install nvm and Node.js version 16
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash && \
    export NVM_DIR="/root/.nvm" && \
    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" && \
    nvm install 16 && \
    nvm use 16
# Set environment variables to make Node.js available in the future
ENV NVM_DIR="/root/.nvm"
ENV NODE_VERSION=16
RUN echo 'source $NVM_DIR/nvm.sh && nvm use $NODE_VERSION' >> /root/.bashrc
# Optional: Run commands to verify installation (you can remove this)
RUN . /root/.nvm/nvm.sh && node -v && npm -v    
RUN curl -O https://packages.microsoft.com/config/ubuntu/$(lsb_release -rs)/packages-microsoft-prod.deb
RUN dpkg -i packages-microsoft-prod.deb && apt-get update && apt-get install -y dotnet-sdk-8.0
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
RUN install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
RUN curl -LO https://github.com/aquasecurity/trivy/releases/download/v0.40.0/trivy_0.40.0_Linux-64bit.deb && \
    dpkg -i trivy_0.40.0_Linux-64bit.deb && \
    rm trivy_0.40.0_Linux-64bit.deb
# docker build -f Dockerfile -t brainupgrade/build-agent-azd:v7 .

