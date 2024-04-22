# Cria-o-do-Modelo-ER-Empresa

Para formalizar as tabelas `dept` e `emp` na prática, precisaremos seguir os comandos SQL que foram fornecidos anteriormente. Aqui está um resumo dos passos que devemos seguir para criar e configurar as tabelas no banco de dados MySQL:

1. **Criar as Tabelas**:
   - Use o comando `CREATE TABLE` para criar as tabelas `dept` e `emp` com as colunas e tipos de dados especificados.

2. **Inserir Dados**:
   - Utilize o comando `INSERT INTO` para adicionar registros nas tabelas `dept` e `emp`.

3. **Configurar Chaves Primárias e Únicas**:
   - Aplique o comando `ALTER TABLE` para adicionar chaves primárias (`PRIMARY KEY`) e chaves únicas (`UNIQUE KEY`) às tabelas, garantindo a unicidade e a integridade dos dados.

4. **Adicionar Chave Estrangeira**:
   - Se necessário, adicione uma chave estrangeira (`FOREIGN KEY`) para estabelecer uma relação entre as tabelas `dept` e `emp`, usando o comando `ALTER TABLE`.

5. **Salvar as Alterações**:
   - Finalize as alterações com o comando `COMMIT` para salvar tudo no banco de dados.

Aqui está um exemplo de como podemos formalizar a tabela `dept` e `emp` com os comandos SQL:

```sql
-- Criação da tabela dept
CREATE TABLE `dept` (
  `DepNume` int(4) NOT NULL,
  `DepNome` char(20) NOT NULL,
  `DepLoca` char(20) NOT NULL,
  `DepOrca` int(12) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- Inserção de dados na tabela dept
INSERT INTO `dept` (`DepNume`, `DepNome`, `DepLoca`, `DepOrca`) VALUES
(10, 'PRESIDENCIA', 'SAO PAULO', 10000),
(20, 'INFORMATICA', 'RIO DE JANEIRO', 500000),
-- (outros registros)

-- Criação da tabela emp
CREATE TABLE `emp` (
  `EmpNume` int(5) NOT NULL,
  `EmpNome` char(30) NOT NULL,
  -- (outras colunas)
  `DepNume` int(4) NOT NULL,
  `EmpAdmi` date NOT NULL,
  `EmpSala` int(10) DEFAULT NULL,
  `EmpComi` int(10) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

-- Inserção de dados na tabela emp
INSERT INTO `emp` (`EmpNume`, `EmpNome`, `EmpGere`, `EmpServ`, `DepNume`, `EmpAdmi`, `EmpSala`, `EmpComi`) VALUES
(1001, 'HORTENCIA OLIVA', 8003, 'BALCONISTA', 40, '1981-02-11', 500, NULL),
-- (outros registros)

-- Configuração de chaves primárias e únicas
ALTER TABLE `dept`
  ADD PRIMARY KEY (`DepNume`),
  ADD UNIQUE KEY `DepNum` (`DepNume`);

ALTER TABLE `emp`
  ADD PRIMARY KEY (`EmpNume`),
  ADD UNIQUE KEY `EmpNum` (`EmpNume`),
  ADD KEY `EmpDep` (`DepNume`);

-- Adição de chave estrangeira (se necessário)
ALTER TABLE `emp`
  ADD FOREIGN KEY (`DepNume`) REFERENCES `dept`(`DepNume`);

-- Salvar as alterações
COMMIT;
```

Execute esses comandos no seu sistema de gerenciamento de banco de dados MySQL para formalizar as tabelas. Devemos ajustar os comandos conforme necessário, especialmente se estivermos trabalhando com um conjunto de dados ou requisitos específicos. Se encontrarmos algum erro durante a execução, verifiquemos a sintaxe para assegurarmos de que todas as dependências, como chaves estrangeiras, estejam corretas e que não haja conflitos com dados existentes.
