FROM mcr.microsoft.com/devcontainers/java:1-21-bookworm

# Evitar prompts interativos
ENV DEBIAN_FRONTEND=noninteractive

# Pacotes necessários
RUN apt-get update && apt-get install -y \
    curl \
    wget \
    unzip \
    ca-certificates \
    gnupg \
    software-properties-common \
    && rm -rf /var/lib/apt/lists/*

# ----------------------------
# Maven 3.9+
# ----------------------------
ARG MAVEN_VERSION=3.9.9

RUN wget -q https://downloads.apache.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
    && tar -xzf apache-maven-${MAVEN_VERSION}-bin.tar.gz -C /opt \
    && ln -s /opt/apache-maven-${MAVEN_VERSION}/bin/mvn /usr/bin/mvn \
    && rm apache-maven-${MAVEN_VERSION}-bin.tar.gz

# ----------------------------
# pnpm 9+
# ----------------------------
RUN npm install -g pnpm@9

# ----------------------------
# Verificação de instalação
# ----------------------------
RUN java -version \
    && mvn -version \
    && node -v \
    && pnpm -v

``