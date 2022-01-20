FROM gitpod/workspace-full

RUN curl -s "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o awscliv2.zip \
    && unzip -q awscliv2.zip \
    && sudo ./aws/install \
    && rm -rf awscliv2.zip aws

COPY configure-ecr-login /usr/local/bin/
RUN sudo install-packages amazon-ecr-credential-helper

RUN curl -sLO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" \
    && sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl \
    && rm kubectl

RUN curl -s https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
