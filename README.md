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