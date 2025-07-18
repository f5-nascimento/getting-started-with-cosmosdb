# Getting Started with Azure Cosmos DB - Table API

Este tutorial mostra como criar uma instância do **Azure Cosmos DB com API Table** e inserir dados diretamente pelo **Data Explorer**, utilizando apenas o portal do Azure.

---

## ✅ Pré-requisitos

- Conta no [Azure](https://portal.azure.com/)
---

## 🧭 Etapas do tutorial

### 1. Acesse o Portal do Azure
- Acesse: [https://portal.azure.com](https://portal.azure.com)
- Faça login com sua conta Microsoft.

---

### 2. Criando a Instância do Cosmos DB com API Table

<img width="1128" height="381" alt="cosmodb" src="https://github.com/user-attachments/assets/2e1efc58-a5bf-45f2-9274-f99f11b101f3" />

- No portal do Azure, pesquise por **Azure Cosmos DB**
- Clique em **Criar**
- Em **Create an Azure Cosmos DB account**, clique em `Others`
- Selecione a opção **Azure Cosmos DB for Table** clicando em `Create`

<img width="1359" height="807" alt="table" src="https://github.com/user-attachments/assets/84bdf909-0224-4bdd-a858-82e309ba2e4c" />


- Na tela **Criar Conta do Microsoft Azure Cosmos DB - Tabela Azure** siga os passos abaixo:
- **Workload Type**, selecione `Learning`
- **Assinatura**: Selecione sua assinatura ativa (ex: `Azure for Students` ou `Azure subscription 1´)
- **Grupo de recursos**: Selecione um existente (ex: `lab-cosmosdb`) ou clique em Criar novo
- **Nome da Conta**: Defina um nome exclusivo para a conta (ex: `table-255`)
- **Availability Zones**: Selecione `Desabilitar`
- **Localização**: Escolha uma região próxima ou mais barata (ex: `West US 3`)
- **Modo de Capacidade**: selecione **Serverless**
- Clique em **Examinar + Criar**
- Clique em **Criar**

---

### 3. Criando uma Tabela no Data Explorer

<img width="1915" height="957" alt="table table" src="https://github.com/user-attachments/assets/d2c74202-98f7-4a3b-b167-0c1698ebb70a" />


- Após a implantação, clique em **Ir para o recursos**.
- No menu lateral, clique em **Data Explorer**
- Clique em **New Table**
- **Table id**: defina um **table id** para a tabela (ex: `cursos`).
- Clique em **OK**
> 💡 Observação:
> O campo Table id é o nome da sua tabela.

---

### 4. Inserindo um Entity

<img width="1642" height="842" alt="table insert" src="https://github.com/user-attachments/assets/c80ccf09-2956-4023-b13f-328624c93fce" />

- Clique em **TablesDB**
- Clique na sua tabela (ex. `cursos`)
- Clique em **Entities**
- Clique em **Add Entity**
- Em **Add Table Row**, defina os valores na coluna **Value** para cada `Property Name`:  
   - **PartitionKey**: `programacao`  
   - **RowKey**: `1`  
- Clique em **+ Add Property** para adicionar novos campos personalizados, por exemplo:  
   - `name` → `"Programação Back-End"`  
   - `carga_horaria` → `80`  
   - `segmento` → `"Qualificação"`  
- Clique em **Add Entity**
> ⚠️ **Observação:**  
> Os campos `PartitionKey` e `RowKey` são **obrigatórios** e, juntos, formam a **chave primária única da linha**.  
> - O `PartitionKey` agrupa registros relacionados (por exemplo, todos os cursos de uma área).  
> - O `RowKey` identifica cada item dentro dessa partição.  
> - A combinação dos dois **não pode se repetir** na tabela.
---

### 5. Atualizando um Entity

<img width="1657" height="841" alt="atualizar table" src="https://github.com/user-attachments/assets/17b94178-5977-4218-bed2-a641e6e5d004" />

- Selecione a Row que deseja atualizar e clique em **Edit Entity**
- Na Tela **Edit Table Entity** altere o `Value` que deseja
- Clique em **Update**


### 6. Deletando Entities

<img width="1257" height="587" alt="deletetable" src="https://github.com/user-attachments/assets/91a9fa3a-7a15-4f13-830a-453856579117" />


- Selecione a Row que deseja atualizar e clique em **Delete Entities**
- Na caixa de confirmação, clique em **Delete**


