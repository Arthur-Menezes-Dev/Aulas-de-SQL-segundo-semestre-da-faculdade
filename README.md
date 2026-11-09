# Aulas de SQl e Banco de Dados do segundo Semestre da Faculdade. 2026

## Codigos-basicos-SQL
Alguns codigos basicos SQL feitos em classe. Repositorio criado em (19/10/2026)

## Codigo 1

-- linguagem sql (structured query language)

-- DML (data manipilation language) Insert Delete Update Select 

-- DDL ( Data definition Language) Create Alter Drop

CREATE DATABASE produtodbd; 

USE produtodbd;

CREATE TABLE produtodb(
	id int,
	produto varchar (25),
	quantidade int,
	preco float
);

ALTER TABLE produtodb ADD COLUMN perecivel char (1);
ALTER TABLE produtodb MODIFY COLUMN produto char (35);
ALTER TABLE produtodb RENAME COLUMN quantidade TO qt;
ALTER TABLE produtodb RENAME TO tb_produto;
ALTER TABLE tb_produto DROP COLUMN preco; 
ALTER TABLE tb_produto ADD COLUMN precos float;

DROP TABLE tb_produto;

CREATE TABLE produtodb(
	id int,
	produto varchar (25),
	quantidade int,
	preco float
);

DROP TABLE produtodb;

desc produtodb;


## Codigo 2

-- Constraints (Restrições ) 
-- unique (Não permite valores repetidos na coluna) 
-- Not Null (Não permite colunas com valores nulos)]
-- Default (Insere um valor padão caso não esteja na inserção ou alteração) 
-- Primary Key 
-- Foreing Key

CREATE TABLE produtodb(
	id int unique not null,
	produto varchar (25) not null,
	quantidade int not null default 100,
	preco float not null
);

DROP TABLE produtodb;

insert into produtodb(id,produto,preco) values(1,'Teclado',35);
insert into produtodb(id,produto,quantidade,preco) values(2,'Monitor',100,600);

select * from produtodb;

desc produtodb;



## Codigo 3

CREATE DATABASE recursos_humanos; 

USE recursos_humanos;

CREATE TABLE funcionario(
	matricula int PRIMARY KEY auto_increment,
    nome varchar(30) not null,
    salario float not null default 1621,
    codigo_departamento int not null,
    foreign key (codigo_departamento) references departamento(codigo)
);

insert into funcionario(nome,codigo_departamento) values
	('Pedro Ramos',1);
    
  insert into funcionario(matricula,nome,codigo_departamento) values
	(5,'Humberto Costa',3);
 	(6,'Janice Arruda',2);   
    
  select * from funcionario;

CREATE TABLE departamento(
codigo int PRIMARY KEY auto_increment,
departamento varchar(15) not null,
ramal int not null
);


insert into departamento(departamento,ramal)values 
	('TI',222),
    ('financeiro', 555),
    ('administrativo', 123);
    
  select * from departamento;

  ## Codigo 4

  CREATE DATABASE Confeitariadb; 

USE Confeitariadb ;

CREATE TABLE produtotb(
	codigo_Produto int PRIMARY KEY auto_increment,
    nome_Produto varchar(30) not null,
	valor_Compra float not null,
    quantidade_Estoque int not null,
    fornecedor int not null,
    foreign key (fornecedor) references fornecedortb(num_Fornecedor)
);

CREATE TABLE fornecedortb(
nome_Fornecedor  varchar(15) ,
num_Fornecedor int not null PRIMARY KEY,
cidade_Fornecedor varchar(15) not null,
estado_Fornecedor varchar (2) not null
);

drop database Confeitariadb ;

insert into departamento(departamento,ramal)values 
	('TI',222),
    ('financeiro', 555),
    ('administrativo', 123);
    
  select * from departamento;

  ## Codigo 5

  create database mercadinho;

use mercadinho;

create table Cliente(
	id int primary key auto_increment,
    nome varchar(30) not null,
    id_endereco int unique not null, 
    foreign key (id_endereco) references Endereco(id)
);

create table Endereco(
	id int primary key auto_increment,
	logradouro varchar(50) not null
);

create table pedido(
	id int primary key auto_increment,
    data date not null,
    valor_total float not null,
    id_cliente int not null, 
    foreign key (id_cliente) references Cliente(id)
);

create table produto(
	id  int primary key auto_increment,
    produto varchar(20) not null,
    preco_unitario float not null

);

create table Itens_pedido(
	id_pedido int not null,
    id_produto int not null,
    quantidade int not null,
    subtotal float not null,
    primary key (id_pedido,id_produto), -- cria chave primaria composta por 2 colunas
    foreign key (id_pedido) references Pedido(id),
    foreign key (id_produto) references Pedido(id), -- Separadas as colunas são foreign, juntas são primary key

);

## Codigo 6 - 19/10/2026

-- ctrl + enter já seleciona a linha

CREATE DATABASE mercadinhomerc ; 

USE  mercadinhomerc ;

CREATE TABLE Cliente(
    codigo INT Primary Key Auto_Increment,
    nome VARCHAR(50) NOT NULL,
    estado VARCHAR(2) NOT NULL,
    email VARCHAR(30) NOT NULL,
    data_nascimento DATE NOT NULL
);

CREATE TABLE Endereco(
    CEP VARCHAR(8) NOT NULL,
    logradouro VARCHAR(40) NOT NULL,
    numero VARCHAR(5) NOT NULL,
    codigo_cliente INT UNIQUE,
    FOREIGN KEY (codigo_cliente) REFERENCES Cliente(codigo)
);

CREATE TABLE Pedido(
    codigo INT PRIMARY KEY Auto_Increment,
    data DATE NOT NULL,
    total FLOAT NOT NULL,
    codigo_cliente INT,
    FOREIGN KEY (codigo_cliente) REFERENCES Cliente(codigo)
);

CREATE TABLE Produto(
    codigo INT PRIMARY KEY Auto_Increment,
    descricao VARCHAR(20) NOT NULL,
    preco_unitario FLOAT NOT NULL
);

CREATE TABLE ItemPedido(
    codPed INT NOT NULL,
    codProd INT NOT NULL,
    quantidade INT NOT NULL,
    subtotal FLOAT NOT NULL,
    PRIMARY KEY (codPed,codProd),
    FOREIGN KEY (codPed) REFERENCES Pedido(codigo),
    FOREIGN KEY (codProd) REFERENCES Produto(codigo)
);

/* DADOS DOS CLIENTES */
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(1,'Maria Francisca','SP','maria@eumesma.com.br','1990-07-15');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(2,'Joana Castro ','SP','joana@hotmail.com.br','2000-07-15');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(3,'Fernando Lima','MG','fernando@gmail.com.br','1990-04-06');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(4,'Janio Francisco','ES','janio@hotmail.com.br','1996-08-10');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(5,'Robson Nascimento','RJ','robson@hotmail.com.br','2000-05-05');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(6,'Luiz Carlos','RJ','luiz@gmail.com.br','1980-07-05');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(7,'Keila Lopes','MG','keila@hotmail.com.br','1983-12-15');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(8,'Paula Silva','PR','paula@empresa.com.br','1990-09-07');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(9,'Roberto Simões','SP','roberto@empresa.com.br','1979-02-03');
INSERT INTO Cliente(codigo,nome,estado,email,data_nascimento) VALUES(10,'Maria das Graças','PR','mariag@eumesma.com.br','1990-07-15');

/* ENDEREÇO DE CADA CLIENTE */
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('12345678','Rua Cariri','145',1);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('23456789','Rua Bastos Limões','234',2);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('34567890','Av Rebouças','1380',3);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('45678901','Av. Consolação','100',4);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('56789012','Rua Gentil de Mais','300',5);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('67890123','Travessa Tumba','476',6);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('78901234','Rua Mandei Cunha','569',7);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('89012345','Av Mantido Vivo','521',8);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('90123456','Rua Sandra Rosa Madalena','2315',9);
INSERT INTO Endereco(CEP,logradouro,numero,codigo_cliente) VALUES('01234567','Travessa Passanao','15',10);

/* PEDIDO */
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(1,'2020-01-02',46.77,1);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(2,'2020-03-03',30.95,1);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(3,'2020-04-10',100.63,2);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(4,'2020-05-12',63.52,2);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(5,'2020-06-15',86.30,2);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(6,'2020-07-07',96.10,3);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(7,'2020-08-20',300.40,4);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(8,'2020-09-20',55.60,4);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(9,'2020-10-26',245.66,4);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(10,'2020-11-28',320.63,4);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(11,'2020-12-30',630.98,5);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(12,'2020-04-08',358.12,5);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(13,'2020-02-06',147.96,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(14,'2020-03-09',368.45,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(15,'2020-04-11',278.23,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(16,'2020-05-16',630.52,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(17,'2020-06-19',128.75,6);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(18,'2020-07-22',635.42,7);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(19,'2020-08-27',322.15,7);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(20,'2020-09-29',745.15,8);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(21,'2020-10-30',520.36,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(22,'2020-11-05',396.46,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(23,'2020-12-07',20.36,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(24,'2020-01-08',985.75,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(25,'2020-02-14',1030.63,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(26,'2020-03-18',423.62,9);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(27,'2020-04-21',460.77,10);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(28,'2020-05-23',412.86,10);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(29,'2020-06-18',98.17,10);
INSERT INTO Pedido(codigo,data,total,codigo_cliente) VALUES(30,'2020-07-30',63.52,10);

/* PRODUTO */
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(1, 'Sabão',8);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(2, 'Sabonete',1.39);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(3, 'Macarrão',2.79);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(4, 'Miojo',1.6);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(5, 'Detergente',1.75);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(6, 'Refrigerante',4);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(7, 'Café',9.5);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(8, 'Chocolate',6.35);
INSERT INTO Produto(codigo,descricao,preco_unitario) VALUES(9, 'Chá',4.55);


/* ITENS DO PEDIDO */
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(1,1,4,32);
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(1,3,3,8.37);
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(1,4,4,6.40);
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(2,1,3,24);
INSERT INTO ItemPedido(codPed,codProd,quantidade,subtotal) VALUES(2,2,5,6.95);



select * from cliente;

select * from pedido where codigo_Cliente=1;

select * from ItemPedido where codped= 1;

select * from produto where codigo in(1,3,4);

select * from Cliente,Pedido where Cliente.codigo = Pedido.codigo_cliente; 

  -- carry é consulta no Banco de Dados
  
-- Esse comando mostra todos os pedidos da cliente maria francisca
select Cliente.codigo,Cliente.nome,Cliente.estado,Cliente.email,Pedido.codigo,Cliente.data_nascimento,Pedido.data,Pedido.total
	from Cliente c,Pedido p 
    where Cliente.codigo = Pedido.codigo_cliente 
		and nome='Maria Francisca'; 
        
-- o c é um apelido eo p tb. c é apelido pra cliente e o p para produto. Assim podemos colocar acima

select c.codigo,c.nome,c.estado,c.email,p.codigo,c.data_nascimento,p.data,p.total
	from Cliente c,Pedido p 
    where c.codigo = p.codigo_cliente 
		and nome='Maria Francisca'; 
        	

-- mostrar todos os produtos do codigo 2
    select ped.data,prod.descricao,prod.preco_unitario,item.quantidade,item.subtotal,item.subtotal,ped.total
		from pedido ped, itemPedido item, Produto prod
        where ped.codigo = item.codped
			and prod.codigo = item.codprod 
            and ped.codigo = 2;
			

-- Padrão ANSI89
-- mostrar todos os pedidos da Maria Francisca e Todos os Produtos de cada Pedido

select cli.nome, ped.codigo, ped.data,prod.descricao,prod.preco_unitario,item.quantidade,item.subtotal,item.subtotal,ped.total
		from Cliente cli, Pedido ped, ItemPedido item, Produto prod
        where cli.codigo = ped.codigo_cliente
        and ped.codigo = item.codped
        and prod.codigo = item.codped
        and cli.nome = 'Maria Francisca';
        
-- modo do professor criar as queries dele 1 from, 2 definir a pk e a fk 3 and 4 select as colunas 













# SQl-Aula-26-10-2026
Aula de Sql do dia 26/10/2026


CREATE DATABASE mercadodoze;

USE mercadodoze;

CREATE TABLE Cliente(
    codigo INT Primary Key Auto_Increment,
    nome VARCHAR(50) NOT NULL,
    estado VARCHAR(2) NOT NULL,
    email VARCHAR(30) NOT NULL,
    data_nascimento DATE NOT NULL
);

CREATE TABLE Pedido(
    codigo INT PRIMARY KEY Auto_Increment,
    data DATE NOT NULL,
    total FLOAT NOT NULL,
    codigo_cliente INT,
    FOREIGN KEY (codigo_cliente) REFERENCES Cliente(codigo)
);

CREATE TABLE Endereco(
    CEP VARCHAR(8) NOT NULL,
    logradouro VARCHAR(40) NOT NULL,
    numero VARCHAR(5) NOT NULL,
    codigo_pedido INT UNIQUE,
    FOREIGN KEY (codigo_pedido) REFERENCES Pedido(codigo)
);

CREATE TABLE Produto(
    codigo INT PRIMARY KEY Auto_Increment,
    descricao VARCHAR(20) NOT NULL,
    preco_unitario FLOAT NOT NULL
);

CREATE TABLE ItemPedido(
    codPed INT NOT NULL,
    codProd INT NOT NULL,
    quantidade INT NOT NULL,
    subtotal FLOAT NOT NULL,
    PRIMARY KEY (codPed,codProd),
    FOREIGN KEY (codPed) REFERENCES Pedido(codigo),
    FOREIGN KEY (codProd) REFERENCES Produto(codigo)
);


-- ==========================================================
-- 1. INSERTS NA TABELA PRODUTO (10 Produtos)
-- ==========================================================
INSERT INTO Produto (descricao, preco_unitario) VALUES
('Arroz 5kg', 25.50),
('Feijão 1kg', 8.50),
('Óleo de Soja 900ml', 6.80),
('Açúcar 1kg', 4.20),
('Café 500g', 16.90),
('Leite 1L', 4.80),
('Macarrão 500g', 3.50),
('Detergente 500ml', 2.20),
('Sabão em Pó 1kg', 12.90),
('Papel Higiênico 12un', 18.00);

-- ==========================================================
-- 2. INSERTS NA TABELA CLIENTE (10 Clientes de vários estados)
-- ==========================================================
INSERT INTO Cliente (nome, estado, email, data_nascimento) VALUES
('Ana Silva', 'SP', 'ana.silva@email.com', '1990-05-15'),
('Bruno Costa', 'RJ', 'bruno.costa@email.com', '1985-10-20'),
('Carla Souza', 'MG', 'carla.souza@email.com', '1998-02-12'),
('Daniel Oliveira', 'SP', 'daniel.oli@email.com', '1975-08-30'),
('Eduarda Lima', 'PR', 'eduarda.lima@email.com', '2001-11-05'),
('Fernando Rocha', 'SC', 'fernando.rocha@email.com', '1992-04-18'),
('Gabriela Santos', 'SP', 'gabi.santos@email.com', '1988-07-22'),
('Heitor Alves', 'RJ', 'heitor.alves@email.com', '1995-01-10'),
('Isabela Mendes', 'MG', 'isabela.mendes@email.com', '2000-09-09'),
('João Pereira', 'RS', 'joao.pereira@email.com', '1982-12-03');

-- ==========================================================
-- 3. INSERTS NA TABELA PEDIDO
-- (Soma exata dos subtotais de ItemPedido)
-- ==========================================================
INSERT INTO Pedido (codigo, data, total, codigo_cliente) VALUES
(1, '2024-01-10', 59.50, 1),   -- Ana Silva (2x Arroz + 1x Feijão)
(2, '2024-01-15', 38.60, 1),   -- Ana Silva (2x Café + 1x Leite)
(3, '2024-01-18', 21.00, 2),   -- Bruno Costa (5x Açúcar)
(4, '2024-01-20', 106.80, 3),  -- Carla Souza (3x Arroz + 1x Óleo + 2x Sabão em Pó)
(5, '2024-01-22', 14.40, 4),   -- Daniel Oliveira (3x Leite)
(6, '2024-02-01', 54.00, 4),   -- Daniel Oliveira (3x Papel Higiênico)
(7, '2024-02-05', 70.00, 4),   -- Daniel Oliveira (2x Arroz + 1x Sabão em Pó + 1x Feijão)
(8, '2024-02-10', 43.80, 5),   -- Eduarda Lima (2x Café + 2x Macarrão + 1x Detergente)
(9, '2024-02-12', 34.00, 6),   -- Fernando Rocha (4x Feijão)
(10, '2024-02-15', 76.50, 7),  -- Gabriela Santos (3x Arroz)
(11, '2024-02-18', 27.20, 7),  -- Gabriela Santos (4x Óleo)
(12, '2024-02-20', 36.00, 8),  -- Heitor Alves (2x Papel Higiênico)
(13, '2024-02-22', 43.60, 9),  -- Isabela Mendes (2x Café + 2x Leite)
(14, '2024-02-25', 102.00, 10),-- João Pereira (4x Arroz)
(15, '2024-02-28', 19.80, 10); -- João Pereira (3x Óleo de Soja)

-- ==========================================================
-- 4. INSERTS NA TABELA ENDERECO (Relação 1:1 com Pedido)
-- ==========================================================
INSERT INTO Endereco (CEP, logradouro, numero, codigo_pedido) VALUES
('01001000', 'Praça da Sé', '100', 1),
('01001000', 'Praça da Sé', '100', 2),
('20040002', 'Rua da Assembleia', '45', 3),
('30130010', 'Avenida Afonso Pena', '500', 4),
('04001001', 'Rua Vergueiro', '1230', 5),
('04001001', 'Rua Vergueiro', '1230', 6),
('04001001', 'Rua Vergueiro', '1230', 7),
('80010000', 'Rua XV de Novembro', '250', 8),
('88010000', 'Felipe Schmidt', '88', 9),
('01310000', 'Avenida Paulista', '1500', 10),
('01310000', 'Avenida Paulista', '1500', 11),
('20010000', 'Rua do Ouvidor', '12', 12),
('30110000', 'Avenida do Contorno', '3000', 13),
('90010000', 'Rua dos Andradas', '400', 14),
('90010000', 'Rua dos Andradas', '400', 15);

-- ==========================================================
-- 5. INSERTS NA TABELA ITEMPEDIDO
-- (subtotal = quantidade * preco_unitario do produto)
-- ==========================================================
INSERT INTO ItemPedido (codPed, codProd, quantidade, subtotal) VALUES
-- Pedido 1 (Total: 59.50)
(1, 1, 2, 51.00), -- 2x Arroz (25.50 * 2)
(1, 2, 1, 8.50),  -- 1x Feijão (8.50 * 1)

-- Pedido 2 (Total: 38.60)
(2, 5, 2, 33.80), -- 2x Café (16.90 * 2)
(2, 6, 1, 4.80),  -- 1x Leite (4.80 * 1)

-- Pedido 3 (Total: 21.00)
(3, 4, 5, 21.00), -- 5x Açúcar (4.20 * 5)

-- Pedido 4 (Total: 106.80)
(4, 1, 3, 76.50), -- 3x Arroz (25.50 * 3)
(4, 3, 1, 6.80),  -- 1x Óleo (6.80 * 1)
(4, 9, 2, 25.80), -- 2x Sabão em Pó (12.90 * 2)

-- Pedido 5 (Total: 14.40)
(5, 6, 3, 14.40), -- 3x Leite (4.80 * 3)

-- Pedido 6 (Total: 54.00)
(6, 10, 3, 54.00),-- 3x Papel Higiênico (18.00 * 3)

-- Pedido 7 (Total: 70.00)
(7, 1, 2, 51.00), -- 2x Arroz (25.50 * 2)
(7, 2, 1, 8.50),  -- 1x Feijão (8.50 * 1)
(7, 9, 1, 12.90), -- 1x Sabão em Pó (12.90 * 1)

-- Pedido 8 (Total: 43.80)
(8, 5, 2, 33.80), -- 2x Café (16.90 * 2)
(8, 7, 2, 7.00),  -- 2x Macarrão (3.50 * 2)
(8, 8, 1, 2.20),  -- 1x Detergente (2.20 * 1)

-- Pedido 9 (Total: 34.00)
(9, 2, 4, 34.00), -- 4x Feijão (8.50 * 4)

-- Pedido 10 (Total: 76.50)
(10, 1, 3, 76.50),-- 3x Arroz (25.50 * 3)

-- Pedido 11 (Total: 27.20)
(11, 3, 4, 27.20),-- 4x Óleo (6.80 * 4)

-- Pedido 12 (Total: 36.00)
(12, 10, 2, 36.00),-- 2x Papel Higiênico (18.00 * 2)

-- Pedido 13 (Total: 43.60)
(13, 5, 2, 33.80),-- 2x Café (16.90 * 2)
(13, 6, 2, 9.60), -- 2x Leite (4.80 * 2)

-- Pedido 14 (Total: 102.00)
(14, 1, 4, 102.00),-- 4x Arroz (25.50 * 4)

-- Pedido 15 (Total: 19.80)
(15, 3, 3, 20.40);-- 3x Óleo (6.80 * 3)



select p.data, p.total, c.nome, c.email 
from Pedido p, Cliente c 
where p.codigo_cliente = c.codigo;


select p.data, p.total, c.nome, c.email 
from Pedido p, Cliente c 
where p.codigo_cliente = c.codigo and c.nome='Ana Silva';


select p.data, p.total, c.nome, c.email, e.cep, e.logradouro, e.numero
	from Pedido p, Cliente c, Endereco e
	where p.codigo_cliente = c.codigo 
		and p.codigo = e.codigo_pedido 
		and c.nome='Ana Silva';





-- mostrar pedidos ana silva
select p.data, p.total, c.nome, c.email, e.cep, e.logradouro, e.numero
	from Pedido p, Cliente c, Endereco e
	where p.codigo_cliente = c.codigo 
		and p.codigo = e.codigo_pedido 
		and c.nome='Ana Silva';
        
        
-- mostrar os produtos do pedido da ana silva na data 10 de janeiro de 2024
select cli.nome, ped.data, pro.descricao,pro.preco_unitario,item.quantidade,item.subtotal, ped.total,end.logradouro,end.numero
	from Cliente cli, Pedido ped, ItemPedido item, Produto pro, Endereco end 
    where ped.codigo_cliente = cli.codigo
		and ped.codigo = end.codigo_pedido
        and ped.codigo = item.codPed
        and ped.codigo = item.codProd
        and cli.nome = 'ana Silva'
        and ped.data = '2024-01-10';
        
        

-- mostrar pedidos ana silva
-- Query (consulta)
-- SQL (structured Query Language - linguagem de consulta estruturada)
select p.data, p.total, c.nome, c.email, e.cep, e.logradouro, e.numero
	from Pedido p, Cliente c, Endereco e
	where p.codigo_cliente = c.codigo 
		and p.codigo = e.codigo_pedido 
		and c.nome='Ana Silva';
        
        
-- mostrar os produtos do pedido da ana silva na data 10 de janeiro de 2024
select cli.nome, ped.data, pro.descricao,pro.preco_unitario,item.quantidade,item.subtotal, ped.total,end.logradouro,end.numero
	from Cliente cli, Pedido ped, ItemPedido item, Produto pro, Endereco end 
    where ped.codigo_cliente = cli.codigo
		and ped.codigo = end.codigo_pedido
        and ped.codigo = item.codPed
        and ped.codigo = item.codProd
        and cli.nome = 'ana Silva'
        and ped.data = '2024-01-10';
        
-- Query (consultas) - PAdrão Ansi 92 (utilizando Joins)

select p.data, p.total, c.nome, c.email
	from Cliente c inner join Pedido p on c.codigo=p.codigo_cliente
    where c.nome='Ana Silva';
        
        


-- mostrar pedidos ana silva
-- Query (consulta)
-- SQL (structured Query Language - linguagem de consulta estruturada)
select p.data, p.total, c.nome, c.email, e.cep, e.logradouro, e.numero
	from Pedido p, Cliente c, Endereco e
	where p.codigo_cliente = c.codigo 
		and p.codigo = e.codigo_pedido 
		and c.nome='Ana Silva';
        
-- Query (consultas) - PAdrão Ansi 92 (utilizando Joins)
        select  p.data, p.total, c.nome, c.email, e.cep, e.logradouro, e.numero
	from Cliente c 
		inner join Pedido p on c.codigo=p.codigo_cliente
        inner join Endereco e on p.codigo=e.codigo_pedido
    where c.nome='Ana Silva';
        
        
-- mostrar os produtos do pedido da ana silva na data 10 de janeiro de 2024
select cli.nome, ped.data, pro.descricao,pro.preco_unitario,item.quantidade,item.subtotal, ped.total,end.logradouro,end.numero
	from Cliente cli, Pedido ped, ItemPedido item, Produto pro, Endereco end 
    where ped.codigo_cliente = cli.codigo
		and ped.codigo = end.codigo_pedido
        and ped.codigo = item.codPed
        and ped.codigo = item.codProd
        and cli.nome = 'ana Silva'
        and ped.data = '2024-01-10';
        



        
	-- 1 select * so escrefvo. as colunas é o ultimo 2 from e vejo a modelagem. 



# Aula do Dia 09/11/2026

-- Funções (Soma "sum", Média "Avarage", Máximo "Max", Minimo "min")
select sum(total) from Pedido;

Sum Pegou a coluna total e somou Tudo. 


-- Funções (Soma "sum", Contagem "Count", Média "Avarage", Máximo "Max", Minimo "min")
select sum(total) Faturamento_Total from Pedido;

select count(total) QtPedidos from Pedido;

select max(total) Maior_Pedido from Pedido;
        
select min(total) Menor_Pedido from Pedido;

select avg(total) Media_Pedido From Pedido;

Também podemos nomear as colunas como vemos aqui. 

select round(avg(total),2) Media_Pedido From Pedido; deixa só 2 casas depois do ponto. 

select round(sum(total),2) Faturamento_Total,
		 count(total) QtPedidos,
         max(total) Maior_Pedido,
         min(total) Menor_Pedido,
         round(avg(total),2) Valor_Medio
	from Pedido;

select  sum(total) total_Faturamento from Pedido Group By codigo_cliente;


select codigo_cliente,
round(sum(total),2) total_Faturamento
 from Pedido Group By codigo_cliente;


 select codigo_cliente,
round(sum(total),2) total_Faturamento
 from Pedido p inner join Cliente c on c.codigo=p.codigo_cliente
 Group By codigo_cliente;

 group by é quando vc vai utilizar uma função e agrupa os itens a serem analisados.


 Select codProd, Sum(quantidade) "Total Vendas(UN)"
	from itemPedido i inner join Produto p on i.codProd=p.codigo
    group by codProd;

Quando eu quiser colocar 2 palavras separadas uma da outra eu apenas coloco elas entre aspas

-- 3) Quantidade de clientes cadastrados por estado
select estado, count(codigo) as "Quantidade Clientes"
from cliente
group by (estado);


oreder by deixar em ordem alfabetica  ou numerica. asc ordem alfabetica ou numerica, desc ordem oposta a asc. o order by vai sempre por ultimo. 

select codigo_cliente,
round(sum(total),2) total_Faturamento
 from Pedido p inner join Cliente c on c.codigo=p.codigo_cliente
 Group By codigo_cliente
 order by Total_Faturamento desc;


 -- distinct (não repete valores de uma coluna na consulta)

select distinct estado from Cliente; 


-- lista dos clientes que já efetuaram pelo menos um pedido
select distinct codigo_cliente from Pedido;

-- lista dos clientes que já efetuaram pelo menos um pedido
select distinct codigo_cliente, c.nome
 from Pedido p inner join Cliente c on c.codigo=p.codigo_cliente;

 -- lista dos produtos quue já foram vendidos pelo menos 1 vez
 
 select distinct codProd, p.descricao
	from itemPedido i inner join Produto p on i.codProd=p.codigo;




	select distinct c.nome, c.email, p.total
from Cliente c inner join Pedido p on c.codigo = p.codigo_cliente
where p.total > (select avg(total) From Pedido);

-- lista dos clientes que já efetuaram produtos que nunca foram vendidos em nenhum pedido registrado. 

select pr.codigo, pr.descricao
from Produto pr left join itemPedido ip on pr.codigo=ip.codprod
where ip.codProd is null;
