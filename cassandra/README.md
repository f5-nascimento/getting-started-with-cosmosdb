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

<img width="1910" height="953" alt="cassandrinha" src="https://github.com/user-attachments/assets/f2ef01d7-e343-4ab6-8105-1fae8b47ed0d" />


- Após a implantação, clique em **Ir para o recursos**.
- No menu lateral, clique em **Data Explorer**
- Clique em **New Table** ou **+ Add Table**
- **Keyspace name**: selecione `Create new` se for o primeiro keyspace ou `Use existing` caso já possua algum.
- Digite um nome para o keyspace (ex: `regencia`).
- **CREATE TABLE**: defina um **table id** para a tabela (ex: `cursos`).
- Insira o código CQL (Cassandra Query Language), exemplo:
```cassandra
 (id int, name text, carga_horaria int, segmento text, PRIMARY KEY (id))
```
- Clique em **OK**
> 💡 Observação:
> O Keyspace name funciona como um "banco de dados lógico" no Cassandra, e deve ser único por instância.
> O campo Table id é o nome da sua tabela.
> O código inserido deve seguir a sintaxe do CQL, a linguagem usada para definir tabelas e manipular dados no Cassandra.

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
