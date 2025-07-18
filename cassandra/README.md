# Getting Started with Azure Cosmos DB - Cassandra API

Este tutorial mostra como criar uma instância do **Azure Cosmos DB com API Cassandra** e inserir dados diretamente pelo **Data Explorer**, utilizando apenas o portal do Azure.

---

## ✅ Pré-requisitos

- Conta no [Azure](https://portal.azure.com/)
---

## 🧭 Etapas do tutorial

### 1. Acesse o Portal do Azure
- Acesse: [https://portal.azure.com](https://portal.azure.com)
- Faça login com sua conta Microsoft.

---

### 2. Criando a Instância do Cosmos DB com API Cassandra

<img width="1128" height="381" alt="cosmodb" src="https://github.com/user-attachments/assets/2e1efc58-a5bf-45f2-9274-f99f11b101f3" />


- No portal do Azure, pesquise por **Azure Cosmos DB**
- Clique em **Criar**
- Em **Create an Azure Cosmos DB account**, clique em `Others`
- Selecione a opção **Azure Cosmos DB for Apache Cassandra** clicando em `Create`


<img width="1395" height="722" alt="telacassandra" src="https://github.com/user-attachments/assets/c713daa9-913e-4fcd-aba0-9958a8611ddc" />


- Em **Create Azure Cosmos DB Account - Choose Architecture**, selecione a opção `Request Unit (RU) database account` e clique em `Create` para continuar.

<img width="1342" height="485" alt="cassandra uru" src="https://github.com/user-attachments/assets/f74503ec-c495-4464-82ed-95d963b8fbd9" />

- Na tela **Criar Conta do Microsoft Azure Cosmos DB - Cassandra** siga os passos abaixo:
- **Workload Type**, selecione `Learning`
- **Assinatura**: Selecione sua assinatura ativa (ex: `Azure for Students` ou `Azure subscription 1´)
- **Grupo de recursos**: Selecione um existente (ex: `lab-cosmosdb`) ou clique em Criar novo
- **Nome da Conta**: Defina um nome exclusivo para a conta (ex: `cassandra-255`)
- **Availability Zones**: Selecione `Desabilitar`
- **Localização**: Escolha uma região próxima ou mais barata (ex: `West US 3`)
- **Modo de Capacidade**: selecione **Serverless**
- Clique em **Examinar + Criar**
- Clique em **Criar**

---

### 3. Criando Keyspace e Tabela no Data Explorer

1. Após a implantação, vá até o recurso criado
2. No menu lateral, clique em **Data Explorer**
3. Clique em **+ New Keyspace**
   - **Keyspace id**: `escola` (exemplo)
   - Clique em **OK**
4. Após o keyspace ser criado, clique em **+ New Table**
   - **Table id**: `alunos`
   - **Partition key**: `id`
   - Clique em **OK**

---

### 4. Inserindo Dados

- Clique na **tabela `alunos`** dentro do keyspace `escola`
- Vá em **Items**
- Clique em **+ New Item**
- Cole o seguinte conteúdo JSON:

```json
{
  "id": "1",
  "nome": "Carla",
  "idade": 20,
  "curso": "TI"
}
```
- Clique em Save
- Repita com outro item se desejar:

```json
{
  "id": "2",
  "nome": "Lucas",
  "idade": 22,
  "curso": "Administração"
}
```

### 5. Visualizando os Dados
- Clique em Items para visualizar todos os registros salvos na tabela alunos.
