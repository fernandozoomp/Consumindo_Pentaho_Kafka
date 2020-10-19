# Consumindo_Pentaho_Kafka
Plug-in do Apache Kafka de etapa do consumidor para Pentaho Kettle.

### Compatibilidade Apache Kafka  ###

O consumidor depende do Apache Kafka 0.8.1.1, o que significa que o broker deve ser da versão 0.8.x ou posterior.

Se você deseja construir o plugin para uma versão diferente do Kafka, você deve
modificar os valores de kafka.version e kafka.scala.version nas propriedades
seção do pom.xml.

### Duração Máxima de Consumo ###


Observe que a duração máxima do consumo é um limite na duração do
etapa inteira, * no * uma leitura individual. Isso significa que se você tiver um máximo
duração de 5000ms, sua transformação irá parar após 5s, seja ou
não existem mais dados e independente de quão rápido cada mensagem é buscada
o tópico. Se você quiser parar de ler mensagens quando o tópico não tiver mais
mensagens, consulte a seção sobre _Empty topic handling_.

### Tratamento de tópico vazio ###

Se você quiser que a etapa pare quando não houver mais mensagens disponíveis no
tópico, marque a caixa de seleção "Stop on empty topic" na caixa de diálogo de configuração. o
tempo limite padrão de espera por mensagens é 1000 ms, mas você pode substituir isso por
definir a propriedade "consumer.timeout.ms" na caixa de diálogo. Se você configurar um
tempo limite sem marcar a caixa, um tópico vazio será considerado uma falha
caso.

### Instalação ###

1. Download ```Consumindo_Pentaho_Kafka``` Zip archive 
2. Extraia o arquivo baixado para *plugins/steps* diretório de sua distribuição Pentaho Data Integration.


### Construindo a partir do código fonte ###

```
mvn clean package
```

