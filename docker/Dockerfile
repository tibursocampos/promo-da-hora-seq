# Use uma versão específica do Ubuntu para estabilidade
FROM ubuntu:22.04

# Instale dependências necessárias
RUN apt-get update && apt-get install -y \
    curl \
    libunwind8 \
    libssl-dev \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Verifique a resolução de DNS para o cdn.datalust.co
RUN apt-get update && apt-get install -y dnsutils && \
    nslookup cdn.datalust.co

# Crie um diretório para o Seq
RUN mkdir -p /seqsvr

# Baixe e extraia o Seq
RUN curl -L https://cdn.datalust.co/seq/latest/docker/seq-linux-x64.tar.gz | tar xz -C /seqsvr

# Defina o diretório de trabalho
WORKDIR /seqsvr

# Defina as permissões necessárias
RUN chmod +x Seq

# Comando para iniciar o Seq
ENTRYPOINT ["/seqsvr/Seq"]
CMD ["--http.port", "80"]
