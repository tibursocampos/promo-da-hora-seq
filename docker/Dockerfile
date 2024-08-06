# Use a imagem oficial do Seq
FROM datalust/seq:latest

# Aceite o EULA
ENV ACCEPT_EULA=Y

# Defina outras variáveis de ambiente conforme necessário
# ENV SEQ_API_CANONICALURI=https://seq.example.com
ENV SEQ_FIRSTRUN_ADMINPASSWORDHASH=changeme

# Exponha as portas necessárias
EXPOSE 80 5341

# Volume para persistir dados do Seq
VOLUME /data

# Iniciar o Seq
CMD ["seq"]