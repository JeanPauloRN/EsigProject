# Usando a imagem oficial do WildFly do Quay
FROM quay.io/wildfly/wildfly:latest

WORKDIR /app

# Copia, builda e move para pasta de deployments o projeto de teste .war
COPY java-example-helloworld-war/ .
RUN jar -cvf helloworld.war *.jsp WEB-INF
RUN mv -f helloworld.war /opt/jboss/wildfly/standalone/deployments/

# Adicionar um usuário de gerenciamento
RUN /opt/jboss/wildfly/bin/add-user.sh admin jB005@eSiG2024 --silent

# Expondo as portas do JBoss
EXPOSE 8090 9990

# Comando para iniciar o JBoss na porta 8090 e habilitar acesso e gerenciamento
CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "192.168.0.100", "-Djboss.bind.address.management=0.0.0.0", "-Djboss.http.port=8090"]
