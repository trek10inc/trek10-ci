FROM public.ecr.aws/amazonlinux/amazonlinux:2023.6.20250218.2
LABEL maintainer="Lucas Pearson <lpearson@trek10.com>"

# add nodejs repo
RUN curl --silent --location https://rpm.nodesource.com/setup_22.x | bash -
RUN yum -y install \
  zip \
  unzip \
  git \
  jq \
  make \
  nodejs \
  openssl \
  openssl-devel \
  python3 \
  python3-devel \
  gcc \
  gcc-c++ \
  libxml2-devel \
  libxslt-devel \
  zlib-devel

# install pip + aws cli + libxml
RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py
RUN pip install awscli --upgrade
RUN pip install lxml

# Move aws v1 to its own command awsv1
RUN mv /usr/local/bin/aws /usr/local/bin/awsv1

# Latest version of aws cli
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf awscliv2.zip ./aws

# update npm to latest version
RUN npm install -g npm

# Install sam cli
RUN pip install aws-sam-cli

# install org formation
RUN npm install -g --production aws-organization-formation@0.9.17
