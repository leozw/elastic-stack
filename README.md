## **Guia de Observability com ELK Stack**

O ELK Stack é uma combinação de três produtos open-source da Elastic: Elasticsearch, Logstash e Kibana. No contexto do Kubernetes, frequentemente incluímos também o Filebeat para coleta de logs. Juntos, eles oferecem uma solução poderosa para log e análise de dados.

- **Elasticsearch**: Um mecanismo de pesquisa e análise distribuído em tempo real. Ele armazena e indexa os logs, tornando-os pesquisáveis.
- **Logstash**: É uma ferramenta de processamento de dados que aceita entradas de várias fontes, transforma os dados e os envia para o Elasticsearch (ou outros destinos).
- **Kibana**: Fornece uma interface de usuário para visualizar, pesquisar e interagir com dados armazenados no Elasticsearch.
- **Filebeat**: Coleta logs dos contêineres em cada nó do Kubernetes e os envia para o Elasticsearch ou Logstash. É leve e opera no lado do cliente, coletando logs e enviando-os para centralizar soluções de armazenamento de log.

No nosso guia, vamos configurar o Filebeat para enviar logs diretamente para o Elasticsearch, sem a necessidade do Logstash.

### **Pré-requisitos:**

- Ter o **`kubectl`** instalado.
- Configuração de **`kubeconfig`** adequada.

**🚀 Configuração**

### **1. Instalando o ECK Operator:**

Para instalar o ECK Operator, que facilitará a implantação e gestão dos produtos Elastic no Kubernetes, execute os comandos a seguir:

```bash
kubectl create -f https://download.elastic.co/downloads/eck/2.9.0/crds.yaml
kubectl apply -f https://download.elastic.co/downloads/eck/2.9.0/operator.yaml
```

### **2. Criando o Namespace para a Stack ELK:**

```bash
kubectl create ns elastic-stack
```

### **3. Instalação do Elasticsearch:**

Ao instalar o Elasticsearch, você terá um mecanismo de busca distribuído que armazena e indexa logs, tornando-os facilmente pesquisáveis e analisáveis.

```bash
kubectl apply -f elasticsearch/elastic-basic.yml -n elastic-stack
```

### **4. Instalação do Kibana:**

Com o Kibana, você terá uma interface gráfica intuitiva para visualizar, pesquisar e interagir com os logs armazenados no Elasticsearch.

```bash
kubectl apply -f kibana/kibana.yml -n elastic-stack
```

### **5. Instalação do Filebeat:**

O Filebeat coleta logs diretamente dos contêineres em cada nó do Kubernetes e os envia para o Elasticsearch. Assim, você garante que os logs sejam centralizados e prontos para análise.

```bash
kubectl apply -f filebeat/filebeat_elastic.yml -n elastic-stack
```

### **🎉 Conclusão:**

Com os passos acima, você terá configurado a stack ELK no seu cluster Kubernetes. Esta combinação de ferramentas proporcionará uma poderosa capacidade de monitoramento, permitindo-lhe pesquisar, visualizar e analisar seus logs em tempo real. Lembre-se de verificar regularmente por atualizações para manter sua stack atualizada e segura.
