# curso_Oracle_PL-SQL_IFRS
Banco de Dados: Oracle PL/SQL - Instituto Federal Rio Grande Do Sul - Carga 20hrs

Conteúdo: Comandos da Linguagem PL/SQL e Blocos Anônimos; Procedures, Functions, Cursores;  Exception, Package e Trigger

 Carga horária: 20 horas

 Módulos: 03

 Metodologia: sem tutoria

 Instituição: IFRS

 Área: informática

 Nível: básico

 Idioma: português

 ## Incio

 1.1 PL/SQL
  O PL/SQL (Procedural Language for SQL) é uma linguagem que permite a criação de blocos de comandos em uma linguagem procedural (if, for, declaração de variáveis) e comandos SQL.
  
  A linguagem PL/SQL utiliza comandos SQL por isso é muito importante o domínio e conhecimento do SQL antes de aprender PL/SQL.
  
  Existem 5 tipos de blocos PL/SQL:
  
  Bloco anônimo: bloco de comandos  PL/SQL que são executados mas não ficam armazenados no banco de dados.
  Procedure: bloco de comandos PL/SQL que ficam armazenados no banco de dados e podem ser executados em outro momento ou chamados de um programa de aplicação. 
  Function: bloco de comandos PL/SQL que retornam um valor na sua chamada e podem ser executados em outro momento ou chamados de um programa de aplicação.
  Package: Pacote contendo procedures e functions.
  Trigger: bloco de comandos PL/SQL que é executado automaticamente quando um determinado evento acontece.
  É importante saber que outros SGBDs (Sistemas Gerenciadores de Banco de Dados) Relacionais permitem a criação de procedures, functions e triggers mas a sintaxe pode ser diferente do PL/SQL.

1.2 Oracle Live
  O Oracle é um dos Sistemas Gerenciadores de Banco de Dados mais utilizados por empresas e instituições de ensino em todo mundo.
  
  O Oracle disponibiliza uma instância do Banco de Dados na núvem, o Oracle Live, para que estudantes possam utilizar este ambiente para aprender SQL (Structured Query Language) e PL/SQL (Procedural Language for SQL).
  
  O Oracle Live pode ser acessado através de um navegador sem a necessidade de instalar qualquer software no computador.
  
  Para ter acesso ao ambiente é necessário realizar um cadastro bem simples no site da Oracle.
  
  Todos os códigos apresentados neste curso foram executados e testados no Oracle Live.

1.3 Script Funcionario-Departamento
Este curso utiliza as tabelas funcionario, departamento e cargo. Os comandos a seguir podem ser executados no Oracle Live para criar e inserir dados nas tabelas Funcionario, departamento e cargo. Também são criadas três sequences uma para cada uma das tabelas.

-- significa que é um comentário

Os comandos drop eliminam os objetos criados.

--CREATE

Create table departamento 
(id_departamento NUMBER CONSTRAINT pk_departamento PRIMARY KEY, 
nome_departamento varchar2(15));

Create table cargo 
(id_cargo NUMBER CONSTRAINT pk_cargo PRIMARY KEY,
nome_cargo VARCHAR2(15),
min_sal NUMBER, 
max_sal NUMBER);

Create table funcionario 
(id_funcionario NUMBER CONSTRAINT pk_funcionario PRIMARY KEY, 
nome_funcionario VARCHAR2(40), 
salario NUMBER, 
id_departamento  NUMBER, 
id_cargo  NUMBER);

alter table funcionario add constraint FK_ID_cargo foreign key (id_cargo) references cargo(id_cargo);
alter table funcionario add constraint FK_ID_departamento foreign key (id_departamento) references departamento (id_departamento);

CREATE SEQUENCE Sfuncionario NOCACHE;
CREATE SEQUENCE Sdepartamento START WITH 100 NOCACHE;
CREATE SEQUENCE Scargo START WITH 300 NOCACHE;

--INSERT

INSERT INTO departamento (id_departamento, nome_departamento) VALUES (sdepartamento.nextval,'Vendas');
INSERT INTO departamento (id_departamento, nome_departamento) VALUES (sdepartamento.nextval,'Contabilidade');

INSERT INTO Cargo (id_cargo, nome_cargo, min_sal, max_sal) 
VALUES (scargo.nextval, 'Vendedor',1000,5000);
INSERT INTO Cargo (id_cargo, nome_cargo, min_sal, max_sal) 
VALUES (scargo.nextval, 'Contador',1000,5000);

INSERT INTO funcionario (id_funcionario, nome_funcionario, salario,id_departamento, id_cargo) VALUES (sfuncionario.nextval,'Pedro',2000,100,300);

INSERT INTO funcionario (id_funcionario, nome_funcionario, salario,id_departamento, id_cargo) VALUES (sfuncionario.nextval,'Ana',3000,100,300);

INSERT INTO funcionario (id_funcionario, nome_funcionario, salario,id_departamento, id_cargo) VALUES (sfuncionario.nextval,'Marta',5000,101,301);

INSERT INTO funcionario (id_funcionario, nome_funcionario, salario,id_departamento, id_cargo) VALUES (sfuncionario.nextval,'Maria',4000,101,301);

--DROP
Drop table funcionario;
Drop table departamento;
Drop table cargo;
Drop sequence SFuncionario;
Drop sequence SDepartamento;
Drop sequence SCargo;











  
