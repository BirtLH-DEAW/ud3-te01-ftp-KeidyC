# Dockerfile para UD03 DEAW
# A partir de la imagen de Ubuntu latest
FROM ubuntu:latest

# Responsable del fichero
LABEL \
	version="1.0" \
	description="Ubuntu latest + proftpd + TE01 UDO3" \
	creationDate="18-12-2024"

# Ejecutamos comandos
RUN \
	apt-get update  \
	&& apt-get install nano\
	&& apt-get -y install proftpd \
	&& apt-get -y install openssl \
	&& apt-get install -y proftpd-mod-crypto \
	&& mkdir -p /etc/proftpd/tls/ \
    # Crea el usuario 'deaw' con un directorio de inicio y shell 'nologin'
    && useradd -m -d /srv/deaw -s /usr/sbin/nologin deaw \
    && echo "deaw:deaw" | chpasswd \
    && chmod 750 /srv/deaw

# Copiamos ficheros necesarios al directorio raíz
COPY conf/proftpd.conf /etc/proftpd/proftpd.conf
COPY conf/tls.conf /etc/proftpd/tls.conf
COPY conf/modules.conf /etc/proftpd/modules.conf

COPY Recursos_Contenedor_2/DefaultRoot_comandos.txt /srv/deaw/DefaultRoot_comandos.txt
COPY Recursos_Contenedor_2/FTP_comandos.txt /srv/deaw/FTP_comandos.txt
COPY Recursos_Contenedor_2/FTPanonimo_comandos.txt /srv/deaw/FTPanonimo_comandos.txt
COPY Recursos_Contenedor_2/README.txt /srv/deaw/README.txt 

COPY conf/cert.pem /etc/proftpd/tls/cert.pem
COPY conf/key.pem /etc/proftpd/tls/key.pem

# Exponemos puertos
EXPOSE 21 50000-50030


