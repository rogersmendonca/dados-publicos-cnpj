# Dados Públicos CNPJ (ETL) 
Processo de Extração-Transformação-Carga (ETL), desenvolvido na plataforma <a href="https://www.knime.com" target="_blank">Knime</a>, que realiza a carga dos <a href="https://www.gov.br/receitafederal/pt-br/assuntos/orientacao-tributaria/cadastros/consultas/dados-publicos-cnpj" target="_blank">Dados Públicos CNPJ</a> (Novo Layout: Março/2021) em um banco de dados relacional.

## Procedimento:
**1. Banco de Dados (criação das tabelas)**
* Criar o banco de dados, se não existir;
* Criar o esquema cnpj;
* Executar [dados_publicos_cnpj_create.ansi.sql](DDL/dados_publicos_cnpj_create.ansi.sql) para criar as tabelas do esquema cnpj. 
Obs: Em vez de executar o script dados_publicos_cnpj_create.ansi.sql (SQL padrão ANSI), é possível executar um script "dados_publicos_cnpj_create" específico dos SGBD [MySQL](DDL/dados_publicos_cnpj_create.mysql.sql), [Oracle](DDL/dados_publicos_cnpj_create.oracle.sql) ou [Microsoft SQL Server](DDL/dados_publicos_cnpj_create.mssqlserver.sql).

**2. Dados Públicos CNPJ (download)**
* Baixar arquivos zip referentes aos <a href="https://www.gov.br/receitafederal/pt-br/assuntos/orientacao-tributaria/cadastros/consultas/dados-publicos-cnpj" target="_blank">Dados Públicos CNPJ</a>, disponibilizados pela Receita Federal.

**3. Knime (execução do ETL)**
* Instalar a plataforma <a href="https://www.knime.com" target="_blank">Knime</a> (versão >= 4.4.0), caso não esteja instalado;
* Abrir o workflow [ETL_DADOS_PUBLICOS_CNPJ](ETL_DADOS_PUBLICOS_CNPJ);
* Configurar o componente "DB Connector";
* Definir os valores das variáveis do workflow (Workflow Variables);
* Executar o workflow [ETL_DADOS_PUBLICOS_CNPJ](ETL_DADOS_PUBLICOS_CNPJ).

**4. Banco de Dados (criação dos índices)**
* Após a conclusão do workflow [ETL_DADOS_PUBLICOS_CNPJ](ETL_DADOS_PUBLICOS_CNPJ), executar [dados_publicos_cnpj_index.sql](DDL/dados_publicos_cnpj_index.sql) para criar os índices das tabelas do esquema cnpj. 
