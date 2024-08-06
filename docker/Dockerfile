# Use uma versão específica do Ubuntu para estabilidade
FROM ubuntu:22.04

# Instale dependências necessárias, incluindo libicu
RUN apt-get update && apt-get install -y \
    curl \
    libunwind8 \
    libssl-dev \
    libicu-dev \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Crie um diretório para o Seq
RUN mkdir -p /seqsvr

# Baixe e extraia o Seq CLI
RUN curl -L https://github.com/datalust/seqcli/releases/download/v2024.3.873/seqcli-2024.3.873-linux-x64.tar.gz \
    -o /seqsvr/seqcli-linux-x64.tar.gz && \
    tar xz -C /seqsvr -f /seqsvr/seqcli-linux-x64.tar.gz && \
    ls -l /seqsvr

# Defina o diretório de trabalho
WORKDIR /seqsvr

# Defina as permissões necessárias
RUN chmod +x seqcli-2024.3.873-linux-x64/seqcli

# Exponha a porta 5341 para comunicação com o Seq server
EXPOSE 5341

# Comando para iniciar o Seq CLI
ENTRYPOINT ["/seqsvr/seqcli-2024.3.873-linux-x64/seqcli"]

# Comando padrão para executar logs, você pode substituir por outro comando conforme necessário
CMD ["log"]
