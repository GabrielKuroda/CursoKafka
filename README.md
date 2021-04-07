# CursoKafka
<br>

## Inicialização

### -Inicia ZooKeeaper

zookeeper-server-start.bat < local zookeeper.properties >
  
### -Inicia Kafka

kafka-server-start.bat < local server.properties >
  
### -OBS

-Sempre iniciar o Zookeeper antes do Kafka

<br>

## Tópicos

### -Vizualizar Tópicos

kafka-topics --bootstrap-server localhost:9092 --list

### -Criar tópico

kafka-topics --bootstrap-server localhost:9092 --create --topic < nome_topico >

### -Deletar tópico (Não funciona no Windows) 
kafka-topics --bootstrap-server localhost:9092 --topic < nome_topico > --delete

#Criar tópico com Replica
kafka-topics --bootstrap-server localhost:9092 --topic < nome_topico > --create --partitions 3 --replication-factor 1

## Mensagem 

### -Enviar mensagem via linha de comando:
kafka-console-producer --broker-list localhost:9092 --topic < nome_topico >

### -Consumir mensagens via linha de comando:
kafka-console-consumer --bootstrap-server localhost:9092 --topic < nome_topico >

### -Consumir mensagens via linha de comando (desde o inicio):
kafka-console-consumer --bootstrap-server localhost:9092 --topic < nome_topico > --from-beginning

### -Consumir mensagens em grupo
kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic < nome_topico > --group < group-name >

### -Mostrar grupos
kafka-consumer-groups --bootstrap-server localhost:9092 --list

### -Enviar mensagem via linha de comando com Chave:
kafka-console-producer --broker-list 127.0.0.1:9092 --topic < nome_topico > --property parse.key-true --property key.separator-,

### -Consumir mensagens via linha de comando sem mostrar a Chave:
kafka-console-consumer --bootstrap-server 127.0.0.1:9092 --topic < nome_topico > --property print.key-false --property key.separator-,

### -OBS

-Para utilizar um Topico e suas Replicas, coloque mais localhosts no bootstrap-server,Ex:
                kafka-console-producer --broker-list localhost:9092,localhost:9093 --topic < nome_topico >
