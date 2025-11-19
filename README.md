# 🍧 Banco de Dados — Projeto Senac (Açaíteria)

Este repositório contém o projeto desenvolvido para a atividade de Banco de Dados do Senac.  
O objetivo foi criar um banco de dados completo utilizando comandos **DDL** e **DML**, aplicados a um **comércio fictício do ramo de açaí**.

---

## 🏪 Sobre o Banco de Dados

O banco foi criado para representar uma **açaíteria**, incluindo tabelas essenciais para o funcionamento de um sistema comercial, como:

- **Produtos**
- **Clientes**
- **Pedidos**
- **Itens do Pedido**

Cada tabela foi estruturada com comandos **DDL**, e posteriormente foram adicionados registros de exemplo utilizando **DML**.

---

## 🧱 DDL — Data Definition Language

Os comandos DDL são responsáveis por **definir a estrutura** do banco, permitindo criar, alterar e excluir bancos e tabelas.

### 📌 Principais comandos DDL

- **CREATE** → cria bancos e tabelas  
- **ALTER** → altera uma tabela existente  
- **DROP** → exclui uma tabela ou banco  

---

## 📝 Exemplos de DDL utilizados no projeto

### **Criando a tabela Produtos, Clientes , Pedidos ItensPedido**
```sql
CREATE TABLE Produtos (
    ProdutoID INT PRIMARY KEY,
    Nome VARCHAR(100) NOT NULL,
    Categoria VARCHAR(50),
    Preco DECIMAL(10,2) NOT NULL,
    Estoque INT NOT NULL
);


CREATE TABLE Clientes (
    ClienteID INT AUTO_INCREMENT PRIMARY KEY,
    Nome VARCHAR(100) NOT NULL,
    Telefone VARCHAR(20),
    Email VARCHAR(100)
);


CREATE TABLE Pedidos (
    PedidoID INT AUTO_INCREMENT PRIMARY KEY,
    ClienteID INT,
    DataPedido DATETIME DEFAULT CURRENT_TIMESTAMP,
    ValorTotal DECIMAL(10,2),

    FOREIGN KEY (ClienteID) REFERENCES Clientes(ClienteID)
);


CREATE TABLE ItensPedido (
    ItemID INT AUTO_INCREMENT PRIMARY KEY,
    PedidoID INT NOT NULL,
    ProdutoID INT NOT NULL,
    Quantidade INT NOT NULL,
    Subtotal DECIMAL(10,2) NOT NULL,

    FOREIGN KEY (PedidoID) REFERENCES Pedidos(PedidoID),
    FOREIGN KEY (ProdutoID) REFERENCES Produtos(ProdutoID)
);

```

### **🍓 DML — Data Manipulation Language**

*Os comandos DML são usados para manipular os dados dentro das tabelas — inserir, consultar, atualizar e remover registros.*

📌 Principais comandos DML

- **INSERT** → insere dados

- **SELECT** → consulta registros

- **UPDATE** → atualiza informações

- **DELETE** → remove registros

``

### **📝 Exemplos de DML utilizados no projeto**

**1 — Insert na tabela Produtos**
```sql
INSERT INTO Produtos (Nome, Categoria, Preco, Estoque)
VALUES
('Açaí Tradicional 300ml', 'Açaí', 12.90, 200),
('Açaí Tradicional 500ml', 'Açaí', 18.90, 150),
('Açaí Kids 200ml', 'Açaí', 9.90, 120);

```

**2 — Insert na tabela Clientes**
```sql
INSERT INTO Clientes (Nome, Telefone, Email)
VALUES
('Fred Mercury', '+55 (12) 98545-3741', 'fredunho.coisogmail.com');

```

**3 — Exemplo de SELECT na tabela Produtos**
```sql
SELECT Preco FROM Produtos WHERE Categoria = 'Açaí';
