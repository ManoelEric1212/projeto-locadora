 # Projeto Locadora de Veículos - SENAI

## Descrição do Problema
Uma locadora de veículos precisa de um sistema simples para gerenciar seu fluxo de carros.O sistema deverá permitir que usuários cadastrados façam login e possam:Cadastrar e gerenciar os carros disponíveis. Registrar movimentações dos veículos (entrada ou saída), indicando a data da movimentação.

O objetivo desta atividade é desenvolver todo o ciclo do projeto: desde a análise e levantamento de requisitos, passando pelo modelo de dados (DER), criação do banco de dados, até a implementação do frontend e backend.

## Entregas da atividade

- [X] Lista de Requisitos Funcionais
- [x] Diagrama Entidade-Relacionamento (DER)
- [X] Modelo Lógico (DER)
- [X] Script de Banco de Dados (MySQL)
- [ ] Criação de dados (Inserts e querys)
- [ ] Interface de Login
- [ ] nterface de Cadastro de Carros (CRUD)
- [ ] Interface de Gerenciamento de Movimentações

# ENTREGAS

### Lista de Requisitos Funcionais:

1. O usuário deverá fazer cadastro
2. O usuário poderá fazer login
3. O usuário poderá cadastrar carros
4. O usuário poderá editar informações dos carros
5. O usuário poderá excluir cadastro de carros
6. O usuário deverá visualizar a lista de veículos
7. O usuário poderá alterar o estado do carro para “Disponível” ou “Alugado”
8. O usuário ao realizar a movimentação, deverá informar o status e data de movimentação

### DER:

<img width="983" height="527" alt="image" src="https://github.com/user-attachments/assets/33f93cae-1e9f-4248-8cd2-ac69dc883eb3" />


### Modelo Lógico:

<img width="781" height="556" alt="image" src="https://github.com/user-attachments/assets/9b29db8a-a373-43de-aa9c-822c0bef5741" />

### Scripts:

```sql

CREATE DATABASE IF NOT EXISTS aluguel_carros;
USE aluguel_carros;


CREATE TABLE Usuario(
      id_usuario INT AUTO_INCREMENT PRIMARY KEY,
      nome VARCHAR(200) NOT NULL,
      email VARCHAR(200) NOT NULL UNIQUE,
      senha VARCHAR(200) NOT NULL
);

CREATE TABLE Carro(
      id_carro INT AUTO_INCREMENT PRIMARY KEY,
      placa VARCHAR(200) NOT NULL UNIQUE,
      chassi VARCHAR(200) NOT NULL UNIQUE,
      modelo VARCHAR(200) NOT NULL
);


CREATE TABLE Movimentacao(
      id_movimentacao INT AUTO_INCREMENT PRIMARY KEY,
      status ENUM('ENTRADA','SAIDA') NOT NULL,
      data DATETIME NOT NULL,
      id_carro INT NOT NULL,
      id_usuario INT NOT NULL,
      FOREIGN KEY (id_carro) REFERENCES Carro(id_carro)
              ON DELETE CASCADE ON UPDATE CASCADE,
      FOREIGN KEY (id_usuario) REFERENCES Usuario(id_usuario)
              ON DELETE CASCADE ON UPDATE CASCADE
);


```

### Querys:


