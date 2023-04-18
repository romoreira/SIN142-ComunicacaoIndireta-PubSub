# SIN142  Comunicação Indireta
## Publicar e Assinar :checkered_flag:
**Objetivos:** Nesta aula será abordado os conceitos de comunicação Indireta em Sistemas Distribuídos utilizando o framework Kafka.
Este exercício lhe dará experiência prática com a construção de um pipeline de processamento de dados do mundo real usando Kafka. Também o ajudará a desenvolver suas habilidades nos principais conceitos e recursos do Kafka, incluindo tópicos, partições, produtores, consumidores, grupos de consumidores e compensações.\
**Requisitos:** Sitema Operacional Linux, IntelliJ IDE, Apache Kafka.

## Passos: :running:

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


## Proposição para Casa :door:

Exercício: Construir um pipeline de processamento de dados em tempo real usando Kafka.\
Neste exercício, você criará um pipeline de processamento de dados usando Kafka que ingere dados de uma fonte de dados, os processa em tempo real e grava os resultados em um coletor de dados.

* Configure um cluster Kafka: configure um cluster Kafka com pelo menos um agente e crie um tópico Kafka para armazenar os dados.

* Produza dados: crie um produtor de dados que gere dados e os envie para o tópico Kafka. Você pode usar uma ferramenta como o produtor de linha de comando do Kafka ou escrever seu próprio produtor usando uma biblioteca cliente Kafka.

* Consuma dados: crie um consumidor de dados que leia os dados do tópico Kafka e os processe em tempo real. Você pode usar uma ferramenta como o consumidor de linha de comando do Kafka ou escrever seu próprio consumidor usando uma biblioteca cliente Kafka.

Processar dados: Implemente a lógica de processamento de dados no consumidor que conte as letas do alfabeto de todos os textos que são produzidos.\ Ex.: O produtor pode ser uma rotina que cria strings de texto aleatórias e o consumidor lê esse pipeline de dados e faz a contagem de letras.

Grave dados: armazene o resultado da contagem de letras geradas pelo produtor. Ex.: pode ser em um DB, pode ser na saída padrão, isto é, apresentar o resultado da contagem ao vivo.
