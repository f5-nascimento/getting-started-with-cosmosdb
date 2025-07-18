# Getting Started with Azure Cosmos DB - Gremlin API

Este tutorial mostra como criar uma instância do **Azure Cosmos DB com API Gremlin** e inserir dados diretamente pelo **Data Explorer**, utilizando apenas o portal do Azure.

---

## ✅ Pré-requisitos

- Conta no [Azure](https://portal.azure.com/)
---

## 🧭 Etapas do tutorial

### 1. Acesse o Portal do Azure
- Acesse: [https://portal.azure.com](https://portal.azure.com)
- Faça login com sua conta Microsoft.

---

### 2. Criando a Instância do Cosmos DB com API Gremlin

<img width="1128" height="381" alt="cosmodb" src="https://github.com/user-attachments/assets/2e1efc58-a5bf-45f2-9274-f99f11b101f3" />


- No portal do Azure, pesquise por **Azure Cosmos DB**
- Clique em **Criar**
- Em **Create an Azure Cosmos DB account**, clique em `Others`
- Selecione a opção **Azure Cosmos DB for Apache Gremlin** clicando em `Create`


<img width="1359" height="702" alt="gremlin" src="https://github.com/user-attachments/assets/48046bbf-1dc1-47bc-ab94-2145306d09ef" />


- Na tela **Criar Conta do Microsoft Azure Cosmos DB - Gremlin (Graph)** siga os passos abaixo:
- **Workload Type**, selecione `Learning`
- **Assinatura**: Selecione sua assinatura ativa (ex: `Azure for Students` ou `Azure subscription 1´)
- **Grupo de recursos**: Selecione um existente (ex: `lab-cosmosdb`) ou clique em Criar novo
- **Nome da Conta**: Defina um nome exclusivo para a conta (ex: `gremlin-255`)
- **Availability Zones**: Selecione `Desabilitar`
- **Localização**: Escolha uma região próxima ou mais barata (ex: `West US 3`)
- **Modo de Capacidade**: selecione **Serverless**
- Clique em **Examinar + Criar**
- Clique em **Criar**

---

### 3. Criando Keyspace e Tabela no Data Explorer

<img width="1914" height="955" alt="gremlin-grpho" src="https://github.com/user-attachments/assets/3e98b8a1-1a82-4b3f-9be4-14bebec3d5b5" />


- Após a implantação, clique em **Ir para o recursos**.
- No menu lateral, clique em **Data Explorer**
- Clique em **New Table**
- **Database id**: selecione `Create new` se for o primeiro keyspace ou `Use existing` caso já possua algum.
- Digite um nome para o Database id (ex: `regencia`).
- **Graph id**: defina um **Graph id** para a tabela (ex: `cursos`).
- **Partition key**: defina um **Partirion Key** para a tabela (ex: `id`).
- Clique em **OK**
> 💡 **Observação:**
> - **Database ID**: é o nome do **banco de dados lógico** que armazenará os grafos criados. Você pode reutilizar um `Database ID` existente ou criar um novo.
> - **Graph ID**: corresponde ao nome do **grafo**, onde os dados (vértices e arestas) serão inseridos. Funciona como uma "tabela" dentro do banco.
> - **Partition Key**: é uma **propriedade dos documentos** (vértices ou arestas) usada para distribuir os dados entre partições internas do Cosmos DB, melhorando a escalabilidade. Exemplo comum: `/id` ou outro campo exclusivo que exista nos seus dados.
> - ⚠️ Certifique-se de que todos os documentos que você inserir tenham o campo definido como chave de partição, senão a inserção falhará.

---

### 4. Inserindo uma Row

<img width="1910" height="953" alt="cassandrinha" src="https://github.com/user-attachments/assets/fbc1c131-778b-4e5d-ad6f-d2c0cbfc160d" />

- Clique no seu keyspace (ex. `regencia`)
- Clique na sua tabela (ex. `cursos`)
- Clique em **Add Row**
- Em **Add Table Row**, na coluna **Value** para respectivos valores para cada `Property Name` 
- Clique em **Add Row**
  
---

### 5. Atualizando uma Row

<img width="1678" height="886" alt="update cassandra" src="https://github.com/user-attachments/assets/3a19a5c3-b8c0-4d7c-897a-268d5d4c1ad9" />

- Selecione a Row que deseja atualizar e clique em **Edit Row**
- Na Tela **Edit Table Entity** altere o `Value` que deseja
- Clique em **Update**
- Clique em **Run Query**


### 6. Deletando uma Row

- Selecione a Row que deseja atualizar e clique em **Delete Rows**
- Na caixa de confirmação, clique em **Delete**
- Clique em **Run Query**

