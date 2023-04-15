# SIN142  Comunicação Indireta
Objetivos: Nesta aula será abordado os conceitos de comunicação Indireta em Sistemas Distribuídos.

Pre-requisitos: Linux Ubuntu, Kafka, IntelliJ IDE.

## Passos:
1. Baixar o [Apache Kafka](https://dlcdn.apache.org/kafka/3.4.0/kafka_2.13-3.4.0.tgz)
2. Extrair a Aplicação `tar -zxvf kafka_2.13-3.4.0.tgz`
3. Rodar a Aplicação:
* `cd kafka_2.13-3.4.0/`
* `bin/zookeeper-server-start.sh config/zookeeper.properties` Execute o Kafka Server
* `bin/kafka-server-start.sh config/server.properties` Execute o Kafka Broker Service
* `KAFKA_CLUSTER_ID="$(bin/kafka-storage.sh random-uuid)"` Crie um Cluster UUID
* `bin/kafka-storage.sh format -t $KAFKA_CLUSTER_ID -c config/kraft/server.properties` Formate o Logs
* `bin/kafka-server-start.sh config/kraft/server.properties` Inicie o Servidor Kafka
* `bin/kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092` Crie um Tópico
* `bin/kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092` Visualize o tópico criado
### Vamos escrever algumas mensagens nesse tópico: quickstart-events
4. `bin/kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092` Inicializa a Aplicação Produtora
A qualquer momento você pode encerrar a aplicação produtora com CRTL + c
### Vamos ler as mensagens que são publicadas no tópico: quickstart-events
5. `bin/kafka-console-consumer.sh --topic quickstart-events --from-beginning --bootstrap-server localhost:9092`
