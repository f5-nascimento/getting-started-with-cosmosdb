# Getting Started with Azure Cosmos DB - MongoDB API

Este tutorial mostra como criar uma instância do **Azure Cosmos DB com API MongoDB** e inserir dados pelo **Azure Databricks**, utilizando apenas o portal do Azure.

---

## ✅ Pré-requisitos

- Conta no [Azure](https://portal.azure.com/)
---

## 🧭 Etapas do tutorial

### 1. Acesse o Portal do Azure
- Acesse: [https://portal.azure.com](https://portal.azure.com)
- Faça login com sua conta Microsoft.

---

### 2. Criando a Instância do Cosmos DB com API MongoDB

<img width="1128" height="381" alt="cosmodb" src="https://github.com/user-attachments/assets/2e1efc58-a5bf-45f2-9274-f99f11b101f3" />

- No portal do Azure, pesquise por **Azure Cosmos DB**
- Clique em **Criar**
- Em **Create an Azure Cosmos DB account**, clique em `Recommended APIs`
- Selecione a opção **Azure Cosmos DB for MongoDB** clicando em `Create`

<img width="1385" height="508" alt="mongo" src="https://github.com/user-attachments/assets/d556188e-a620-4b12-89e6-e99f404b73f0" />

- Em **Create Azure Cosmos DB Account - Choose Architecture**, selecione a opção `Request Unit (RU) database account` e clique em `Create` para continuar.

<img width="1343" height="491" alt="mongoarch" src="https://github.com/user-attachments/assets/aaf2d81a-f66f-45cf-a116-cf38b93ec3b9" />


- Na tela **Criar Conta do Microsoft Azure Cosmos DB - Tabela Azure** siga os passos abaixo:
- **Workload Type**, selecione `Learning`
- **Assinatura**: Selecione sua assinatura ativa (ex: `Azure for Students` ou `Azure subscription 1´)
- **Grupo de recursos**: Selecione um existente (ex: `lab-cosmosdb`) ou clique em Criar novo
- **Nome da Conta**: Defina um nome exclusivo para a conta (ex: `mongodb-255`)
- **Availability Zones**: Selecione `Desabilitar`
- **Localização**: Escolha uma região próxima ou mais barata (ex: `West US 3`)
- **Modo de Capacidade**: selecione **Serverless**
- Clique em **Examinar + Criar**
- Clique em **Criar**

---

### 3. Criando uma Collection no Data Explorer

<img width="1919" height="958" alt="mongo-collection" src="https://github.com/user-attachments/assets/231940a2-c4f8-4f2d-ad20-7a07a2fbf863" />


- Após a implantação, clique em **Ir para o recursos**.
- No menu lateral, clique em **Data Explorer**
- Clique em **New Collection**
- **Database name**: selecione `Create new` se for o primeiro database ou `Use existing` caso já possua algum (ex: `regencia`).
- **Collection id**: defina um **Collection id** para a tabela (ex: `cursos`).
- **Sharding**: selecione ´Sharded´
- **Shard Key**: defina uma chave (ex: `segmento`)
- Clique em **OK**

---

### 4. Inserindo um Documento via Data explorer

<img width="1877" height="482" alt="mongosave" src="https://github.com/user-attachments/assets/f06d62af-ffcb-471a-8036-ff2e29a41d11" />

- Clique na sua tabela (ex. `cursos`)
- Clique em **Documents**
- Clique em **New Documents** 
- Escreva o arquivo JSON para adicionar novos campos personalizados, por exemplo:  

```json
{
	"nome" : "Programador Back-End",
	"carga_horaria" : 80,
	"segmento" : "Qualificação"
}
```
- Clique em **Save**
> - O **Data Explorer** do Azure Cosmos DB **não permite inserir múltiplos documentos ao mesmo tempo** usando a interface padrão de criação de documentos (`New Document`).
> - Para resolver essa questão, **usaremos o Azure Databricks** para realizar as operações sobre documentos na API MongoDB do Cosmos DB.


---

## 5. Criando o Workspace no Azure Databricks

<img width="1517" height="355" alt="azdatabricks" src="https://github.com/user-attachments/assets/3fe73abf-fb05-4bc8-8b6a-5ea38194affc" />

- No campo de busca do portal, digite **Azure Databricks**
- Clique no ícone conforme a imagem acima.
- Após o redirecionamento para uma nova tela, clique em **Criar**
- Na tela **Criar um workspace do Azure Databricks**, preencha os passos:
- **Assinatura**: Selecione sua assinatura ativa (ex: `Azure for Students` ou `Azure subscription 1`)
- **Grupo de recursos**: Selecione um existente (ex: `lab-databricks`) ou clique em **Criar novo**
- **Nome do Workspace**: Defina um nome exclusivo para o workspace (ex: `work-databricks`)
- **Região** (ex: West US 3)
- **Tipo de Preço**: Selecione a opção `Avaliação`
- **Nome do Grupo de Recursos Gerenciados**: deixe em branco (será preenchido automaticamente)
- Clique em **Revisar + Criar**
- Após a validação, clique em **Criar**

---

## 6. Acessando o Azure Databricks

<img width="1877" height="747" alt="workpace" src="https://github.com/user-attachments/assets/6da50ec1-07bb-4270-8d83-79be594434c7" />

- Após a implantação, clique em **Ir para o recurso**
- Clique em **Iniciar workspace**
- Você será redirecionado para o ambiente Databricks

---

## 7. Criando um notebook

<img width="1782" height="637" alt="notebooks" src="https://github.com/user-attachments/assets/a296c932-e652-44c9-8f0c-61b843041920" />

- No menu lateral cliquem em **+ Novo**
- Depois clique em **Notebook**
- Copie o código abaixo no notebook:
  
```python

# Conexão ao Azure Cosmos DB com API MongoDB
!pip install pymongo
from pymongo import MongoClient, errors

# String de conexão - substitua pelo seu valor real
mongo_uri = "mongodb://<USERNAME>:<PASSWORD>@<HOST>:<PORT>/?ssl=true&replicaSet=globaldb&retrywrites=false"

try:
    # Criando o cliente
    client = MongoClient(mongo_uri, serverSelectionTimeoutMS=5000)

    # Conectando ao banco e coleção
    db = client["regencia"]         # nome do banco
    collection = db["cursos"]           # nome da coleção

    # Teste simples: contar documentos
    total = collection.count_documents({})
    print(f"Conexão bem-sucedida! Total de documentos na coleção: {total}")

except errors.ServerSelectionTimeoutError as err:
    print("❌ Erro ao conectar com o Cosmos DB:")
    print(err)
except Exception as e:
    print("❌ Outro erro ocorreu:")
    print(e)


```

---

## 8. Coletando os dados do MongoDB

<img width="1900" height="893" alt="mongo-uri" src="https://github.com/user-attachments/assets/4310dd8f-c4cc-40c7-acd4-a925d6a7045d" />

- No painel lateral do seu MongoDB acesse a opção **Configurações**
- Clique em **Cadeia de Conexão**  
> Extraia as seguintes informações para conexão:

| Parâmetro | Informações do MongoDB                             | 
|-----------|---------------------------------------------|
| username      | `mongodb-255` |
| password  | `Cole em PRIMARY PASSWORD`                           |
| host      | `mongodb-255.mongo.cosmos.azure.com`                              |
| port  | `10255`                          |



## 9. Executando o notebook


<img width="1819" height="821" alt="mongo-serveless" src="https://github.com/user-attachments/assets/b3d8d0c4-d79c-4efa-87c0-a12bde1f63af" />


- Altere o código com os dados da sua URL, siga o exemplo abaixo

```python
# Configurações do banco
mongo_uri = "mongodb://mongodb-255:Cole aqui o valord do seu PRIMARY PASSWORD@mongodb-255.mongo.cosmos.azure.com:10255/?ssl=true&replicaSet=globaldb&retrywrites=false"
```
- Clique em **Ligar**
- Selecione a opção **Servless**
- Clique em **Executar célula**
