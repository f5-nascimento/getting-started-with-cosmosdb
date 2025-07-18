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

### 3. Criando um Graph

<img width="1914" height="955" alt="gremlin-grpho" src="https://github.com/user-attachments/assets/3e98b8a1-1a82-4b3f-9be4-14bebec3d5b5" />

- Após a implantação, clique em **Ir para o recursos**.
- No menu lateral, clique em **Data Explorer**
- Clique em **New Graph**
- **Database id**: selecione `Create new` se for o primeiro keyspace ou `Use existing` caso já possua algum.
- Digite um nome para o Database id (ex: `regencia`).
- **Graph id**: defina um **Graph id** para a tabela (ex: `cursos`).
- **Partition key**: defina um **Partirion Key** para a tabela (ex: `segmento`).
- Clique em **OK**
> 💡 **Observação:**
> - **Database ID**: é o nome do **banco de dados lógico** que armazenará os grafos criados.
> - **Graph ID**: é o nome do **grafo**, onde você armazenará os vértices e arestas.
> - **Partition Key**: é uma propriedade dos seus dados que será usada como chave de partição. **Evite usar** `/id` e `/label`, pois não são permitidos pela API Gremlin.
> - ➕ Use uma propriedade personalizada como `/categoria`, `/tipo`, `/grupo`, ou qualquer outro campo exclusivo presente nos dados do grafo.

---

### 4. Inserindo um Graph

<img width="1652" height="849" alt="gremlin-insert" src="https://github.com/user-attachments/assets/eae474c8-d619-4c90-9777-812833f8731e" />

- Clique no **New Vertex**
- Em **New Vertex**, defina um **Value** para o `Label`:
- **Key**: defina um **Value** para a sua principal `Key` (ex: ´segmento´ → ´Qualificação´):
- Clique em **+ Add Property** para adicionar novos campos personalizados, por exemplo:  
   - `name` → `Programação Back-End` → `string`
   - `carga_horaria` → `80` → `number`
- Clique em **OK**
  
---

### 5. Inserindo via Gremlin Query

<img width="1641" height="751" alt="gremlin-insert2" src="https://github.com/user-attachments/assets/c5f43bdb-6e61-4633-8da0-66d431b7fd6b" />


- Para adicionar via Query, digite
  ```gremlin
  g.addV('curso').property('segmento', 'Qualificação').property('nome', 'Programador Front-End').property('carga_horaria', 100)
  ```
- Clique em **Execute Gremlin Query**
- Clique em **JSON**
  
---

### 6. Consultando via Gremlin Query

- Para consultar todos os vértices, digite:
  ```gremlin
  g.V()
  ```
- Clique em **Execute Gremlin Query**
> Para consultas mais específicas, utilize filtros com hasLabel ou has. Exemplos:
> - g.V().hasLabel('curso')  **Retorna todos os vértices com o label 'curso'**
> - g.V().has('segmento', 'Qualificação') **Retorna vértices com a propriedade segmento igual a 'Qualificação'**
> - g.V().has('carga_horaria', 80) **Retorna vértices com carga_horaria igual a 80**


---

### 7. Atualizando via Gremlin Query

- Para atualziar via Query, digite
  ```gremlin
   g.V().has('name', 'Programador Back-End').property('carga_horaria', 200)
  ```
- Clique em **Execute Gremlin Query**
- Clique em **JSON**

---

### 8. Deletando via Gremlin Queryuma Row

- Para deletar via Query, digite
```gremlin
   g.V().has('name', 'Programador Back-End').drop()
```
- Clique em **Execute Gremlin Query**
- Clique em **JSON**

> Para deleções mais específicas, utilize filtros com hasLabel ou has. Exemplos:
> - g.V().drop() **Deleta todos os vértices do grafo.**
> - g.V().hasLabel('curso').drop() **Deleta todos os vértices com o label 'curso'**
