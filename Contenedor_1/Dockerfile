# Dockerfile para UD03 DEAW
# A partir de la imagen de Ubuntu latest
FROM ubuntu:latest

# Responsable del fichero
LABEL \
	version="1.0" \
	description="Ubuntu:latest + Proftpd + TE01 UDO3" \
	creationDate="17-12-2024"

# Ejecutamos comandos
RUN \
	apt-get update  \
	&& apt-get install nano \
	&& apt-get -y install proftpd \
    && mkdir -p /srv/ftp/Recursos_Contenedor_1/
	
# Copiamos ficheros necesarios al directorio raíz
COPY Recursos_Contenedor_1/css_index /srv/ftp/Recursos_Contenedor_1/
COPY Recursos_Contenedor_1/index.html /srv/ftp/Recursos_Contenedor_1/

COPY conf/proftpd.conf /etc/proftpd/proftpd.conf


# Exponemos puertos
EXPOSE 21 50000-50030
