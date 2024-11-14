FROM ruby:3.0

# Instala Fluentd
RUN gem install fluentd -v '1.17.1'

RUN ["gem", "install", "elasticsearch", "--no-document", "--version", "7.17.0"]
RUN ["gem", "install", "fluent-plugin-elasticsearch", "--no-document", "--version", "4.0.1"]

# Crea el directorio para la configuración de Fluentd
RUN mkdir -p /fluentd/etc

# Copia el archivo de configuración de Fluentd al contenedor
COPY fluent.conf /fluentd/etc/fluent.conf

# Expone el puerto que usará Fluentd
EXPOSE 24224

# Comando para iniciar Fluentd
CMD ["fluentd", "-c", "/fluentd/etc/fluent.conf", "-p", "/fluentd/plugins"]
