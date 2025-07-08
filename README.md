# hive
instruções para instalação, configuração e execução da aplicação Hive, além dos scripts para criação e povoamento do banco de dados.

Índice

Pré-requisitos

Instalação

Configuração do Banco de Dados

Scripts de Banco de Dados

Variáveis de Ambiente

Execução da Aplicação

Execução de Testes

Estrutura do Projeto

Pré-requisitos

Python 3.8+

PostgreSQL 12+

Git

Instalação

Clone o repositório:

git clone https://github.com/seu-usuario/hive.git
cd hive

Crie e ative um ambiente virtual:

python3 -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows

Instale as dependências:

pip install -r requirements.txt

Configuração do Banco de Dados

Crie o banco de dados no PostgreSQL:

psql -U seu_usuario
CREATE DATABASE hive_db;
\q

Atualize as credenciais no arquivo .env (veja Variáveis de Ambiente).

Scripts de Banco de Dados

schema.sql: contém os comandos para criar as tabelas principais:

usuário

desenvolvedora

jogo

compra

item_compra

biblioteca

avaliação

Execute:

psql -U seu_usuario -d hive_db -f db/schema.sql

seed.sql: contém instruções para inserir dados de exemplo (usuários, jogos etc.):

psql -U seu_usuario -d hive_db -f db/seed.sql

Os arquivos estão localizados em db/.

Variáveis de Ambiente

FLASK_APP=app.py
FLASK_ENV=development
DATABASE_URL=postgresql://<usuario>:<senha>@localhost:5432/hive_db
SECRET_KEY=sua_chave_secreta

Crie um arquivo .env na raiz do projeto com as seguintes variáveis:

FLASK_APP=app.py
FLASK_ENV=development
DATABASE_URL=postgresql://<usuario>:<senha>@localhost:5432/hive_db
SECRET_KEY=sua_chave_secreta

Execução da Aplicação

Com o ambiente virtual ativo e o banco configurado, execute:

flask run

Acesse em: http://localhost:5000
Execução de Testes

Estrutura do Projeto
/.
├── app.py
├── requirements.txt
├── .env
├── db/
│   ├── schema.sql
│   └── seed.sql
├── templates/
│   ├── login.html
│   └── ...
├── static/
│   └── css/
└── tests/
    └── test_app.py
