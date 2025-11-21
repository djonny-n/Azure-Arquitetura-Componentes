# Azure - Arquitetura de Componentes

## Introdução

Este repositório contém um projeto prático de **arquitetura de componentes no Microsoft Azure**, focando em padrões de design, melhores práticas e implementações reais para profissionais que buscam dominar a plataforma Azure.

O objetivo principal é fornecer exemplos concretos, diagramas de arquitetura e documentação detalhada dos componentes fundamentais do Azure.

---

## Índice

1. [Conceitos Fundamentais](#conceitos-fundamentais)
2. [Componentes Principais do Azure](#componentes-principais-do-azure)
3. [Padrões de Arquitetura](#padrões-de-arquitetura)
4. [Implementações Reais](#implementações-reais)
5. [Melhores Práticas](#melhores-práticas)
6. [Recursos Adicionais](#recursos-adicionais)

---

## Conceitos Fundamentais

### O que é Arquitetura em Nuvem?

Arquitetura em nuvem é o design de sistemas de TI construídos sobre plataformas em nuvem como Azure. Envolve:

- **Scalability**: Capacidade de crescer com a demanda
- **Reliability**: Disponibilidade e recuperação de falhas
- **Security**: Proteção de dados e acesso
- **Performance**: Otimização de velocidade e latência
- **Cost Optimization**: Gerenciamento eficiente de custos

### Pilares de Arquitetura do Azure

#### 1. **Confiabilidade (Reliability)**
- Múltiplas regiões e zonas de disponibilidade
- Recuperação de desastres (DR)
- Backup e redundancy

#### 2. **Segurança (Security)**
- Encriptação em trânsito e em repouso
- Controle de acesso (RBAC)
- Audit logging
- Azure Security Center

#### 3. **Eficiência Operacional (Operational Excellence)**
- Automação de deploys
- Monitoramento e logs
- DevOps practices
- Infrastructure as Code (IaC)

#### 4. **Excelencia de Performance (Performance Efficiency)**
- Escalabilidade horizontal e vertical
- Caching e CDN
- Otimização de banco de dados

#### 5. **Otimização de Custos (Cost Optimization)**
- Right-sizing de recursos
- Reserved Instances
- Monitoramento de gastos
- Auto-scaling

---

## Componentes Principais do Azure

### Computa (Compute)

#### **Azure Virtual Machines (VMs)**
- Máquinas virtuais IaaS
- Flexibilidade total de SO e software
- Cobrança por hora/minuto

```
Uso: Legacy apps, custom software, full control
```

#### **Azure App Service**
- Hospedagem de web apps e APIs
- PaaS - gerenciamento reduzido
- Suporta: .NET, Java, Node, Python, Ruby

```
Uso: Web applications, microservices, REST APIs
```

#### **Azure Container Instances (ACI)**
- Containers sem orquestração
- Rápido deployment
- Ideal para cargas puntuais

```
Uso: Batch jobs, quick containers, testing
```

#### **Azure Kubernetes Service (AKS)**
- Orquestração profissional de containers
- Escalabilidade autómatica
- Gerenciado pelo Azure

```
Uso: Aplicacoes em container scale-out
```

#### **Azure Functions**
- Serverless computing
- Cobrança por execução
- Escalabilidade instantânea

```
Uso: Event-driven workloads, APIs de baixa latência
```

### Armazenamento (Storage)

#### **Azure Storage Account**
- Blob Storage: objetos/arquivos
- File Share: SMB/NFS compartilhado
- Queue: mensagens assíncronas
- Table: NoSQL simples

```
Uso: Data lake, backups, media files
```

#### **Azure SQL Database**
- Banco relacional gerenciado
- Automatic backups
- Point-in-time restore

```
Uso: Aplicações transacionais
```

#### **Azure Cosmos DB**
- NoSQL glob almente distribuído
- Múltiplos models (doc, key-value, graph)
- Latência baixa em qualquer lugar

```
Uso: Apps globais, IoT, real-time analytics
```

### Networking

#### **Virtual Network (VNet)**
- Rede isolada na nuvem
- Subnets e security groups
- Conectividade híbrida com on-premises

#### **Azure Load Balancer**
- Distribuição de tráfego
- Alta disponibilidade
- Camada 4 (TCP/UDP)

#### **Azure Application Gateway**
- Load balancing Layer 7 (HTTP/HTTPS)
- Web Application Firewall (WAF)
- Path-based routing

#### **Azure Traffic Manager**
- DNS-based load balancing
- Failover automático entre regiões
- Geo-routing

### Bancos de Dados

#### **Azure Database for MySQL/PostgreSQL**
- Bancos relacionais gerenciados
- Open-source
- Automatic scaling

#### **Azure Cache for Redis**
- Cache em memória
- Reduz latência
- Suporta estruturas complexas

---

## Padrões de Arquitetura

### 1. **N-Tier Architecture**
```
Presentation Tier (Web/API)
    |
    v
Business Logic Tier (App Service)
    |
    v
Data Tier (SQL/Database)
```

**Benefícios**:
- Separação de responsabilidades
- Fácil manuitenção
- Escalabilidade por tier

### 2. **Microservices**
```
Multiplos serviços independentes
    |
    +--- User Service (AKS/App Service)
    +--- Order Service (AKS/App Service)
    +--- Payment Service (AKS/App Service)
    +--- Inventory Service (AKS/App Service)
    |
    v
API Gateway
```

**Benefícios**:
- Desenvolvimento independente
- Escalabilidade granular
- Resiliência melhorada

### 3. **Event-Driven Architecture**
```
Event Source
    |
    v
Event Hub/Service Bus
    |
    +--- Consumer 1 (Function)
    +--- Consumer 2 (Function)
    +--- Consumer 3 (Logic App)
```

**Benefícios**:
- Desacoplamento
- Escalabilidade assincrôna
- Tempo real processing

### 4. **Serverless Architecture**
```
Trigger (HTTP/Timer/Queue)
    |
    v
Azure Functions (Auto-scale)
    |
    v
Managed Services
(Cosmos DB, Storage, etc.)
```

**Benefícios**:
- Sem infraestrutura
- Pay-per-execution
- Auto-scaling

---

## Implementações Reais

### Exemplo 1: E-Commerce Platform

**Arquitetura**:
- **Frontend**: Azure App Service ou Static Web App
- **API**: Azure App Service or Azure Functions
- **Database**: Azure SQL + Cosmos DB
- **Cache**: Azure Cache for Redis
- **Storage**: Azure Blob Storage (imagens)
- **CDN**: Azure CDN
- **Search**: Azure Cognitive Search

**Alta Disponibilidade**:
- Múltiplas regiões
- Load Balancer
- Automatic failover
- Disaster Recovery plan

### Exemplo 2: Real-Time Analytics

**Arquitetura**:
- **Ingestion**: Event Hubs or IoT Hub
- **Stream Processing**: Stream Analytics
- **Storage**: Cosmos DB or Data Lake
- **Visualization**: Power BI
- **Orchestration**: Data Factory

---

## Melhores Práticas

### 1. **Segurança**
- [ ] Usar RBAC para acesso
- [ ] Ativar Azure AD
- [ ] Encriptar dados em repouso
- [ ] Usar VNets privadas
- [ ] Monitorar com Security Center

### 2. **Performance**
- [ ] Implementar caching
- [ ] Usar CDN
- [ ] Otimizar queries
- [ ] Monitorar métricas
- [ ] Auto-scaling habilitado

### 3. **Custo**
- [ ] Use Reserved Instances
- [ ] Right-sizing de recursos
- [ ] Auto-shutdown de dev/test
- [ ] Monitorar gastos
- [ ] Usar Azure Cost Management

### 4. **Operacional**
- [ ] Infrastructure as Code (Terraform/ARM)
- [ ] CI/CD pipelines
- [ ] Monitoring e alertas
- [ ] Backup automatizado
- [ ] Disaster recovery plan

---

## Recursos Adicionais

### Documentação Oficial
- [Microsoft Learn - Azure Fundamentals](https://learn.microsoft.com/pt-br/training/paths/azure-fundamentals/)
- [Azure Architecture Center](https://learn.microsoft.com/pt-br/azure/architecture/)
- [Well-Architected Framework](https://learn.microsoft.com/pt-br/azure/architecture/framework/)

### Ferramentas
- [Azure Portal](https://portal.azure.com)
- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/)
- [Azure DevOps](https://dev.azure.com)
- [Visual Studio Code + Azure Extensions](https://code.visualstudio.com/)

### Certificações
- AZ-900: Azure Fundamentals
- AZ-104: Azure Administrator
- AZ-305: Designing Microsoft Azure Infrastructure Solutions

---

## Contribuindo

Sugestões e melhorias são bem-vindas! Sinta-se livre para:
- Adicionar novos padrões
- Compartilhar implementações
- Reportar erros ou inexatidões

---

## Autor

Projeto criado para o laboratório de **Componentes de Arquitetura do Azure** da formação **AZ-900** na plataforma DIO.

**Última atualização**: Dezembro 2024

---

*Recursos educacionais para estudantes e profissionais de Azure* 🚀
