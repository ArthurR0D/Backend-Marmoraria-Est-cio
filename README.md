# Backend-Marmoraria-Est-cio
Introdução
Este projeto é o backend de uma aplicação web para gerenciar uma loja de mármores. Ele fornece uma API RESTful para operações como autenticação, gerenciamento de clientes, pedidos, pagamentos, entregas, estoque e tipos de mármores. O backend é desenvolvido em Flask e utiliza MySQL como banco de dados, com autenticação via JWT para segurança. Este projeto foi criado para um trabalho de faculdade em grupo, com o objetivo de criar uma solução completa para gerenciar as operações de uma marmoraria.

Instalação
Para configurar o ambiente de desenvolvimento, siga os passos abaixo:

Pré-requisitos
Python 3.x (recomendado Python 3.11 ou superior)
MySQL Server (com um banco de dados chamado loja)
Pip (gerenciador de pacotes Python)
Git (para clonagem do repositório, se aplicável)
Dependências
Instale as dependências do projeto executando o seguinte comando no terminal:

bash

Copiar
pip install -r requirements.txt
Se o arquivo requirements.txt não existir, crie-o com:

bash

Copiar
pip freeze > requirements.txt
Certifique-se de que as seguintes bibliotecas estão incluídas:

Flask
Flask-SQLAlchemy
Flask-CORS
Flask-JWT-Extended
Werkzeug
Flask-Migrate
python-dotenv
pymysql
Configuração do Ambiente Virtual
Para isolar as dependências do projeto e evitar conflitos, crie um ambiente virtual:

bash

Copiar
python -m venv venv
Ative o ambiente virtual:

No Linux/Mac: source venv/bin/activate
No Windows: venv\Scripts\activate
Após ativar, instale as dependências conforme descrito acima.

Configuração do Banco de Dados
Certifique-se de que o MySQL está rodando e crie um banco de dados chamado loja.
Configure as variáveis de ambiente em um arquivo .env no diretório raiz do projeto:
text

Copiar
SQLALCHEMY_DATABASE_URI=mysql+pymysql://root:JulietaeLana1@@127.0.0.1/loja?charset=utf8mb4
Substitua root pelo seu usuário MySQL, JulietaeLana1@ pela sua senha, 127.0.0.1 pelo host do seu banco de dados (use localhost se for local) e loja pelo nome do banco de dados.
Nota importante: Não commit o arquivo .env no Git; adicione-o ao .gitignore para segurança.
As tabelas do banco de dados serão criadas automaticamente na primeira execução, com base nos modelos SQLAlchemy. Se preferir, use Flask-Migrate para gerenciar migrações:
bash

Copiar
flask db init
flask db migrate
flask db upgrade
Configuração no PyCharm
Se estiver usando o PyCharm:

Abra o projeto em File > Open e selecione a pasta com backend_marmore.py.
Configure o interpretador em Settings > Project > Python Interpreter, apontando para o ambiente virtual criado (venv).
Instale dependências via PyCharm, se necessário, em Settings > Python Interpreter > + > pymysql, etc.
Verifique se o .env está configurado corretamente para o banco de dados.
Execução
Abra o terminal e navegue até o diretório do projeto.
Certifique-se de que o ambiente virtual está ativado (se usado).
Execute o aplicativo Flask:
bash

Copiar
python backend_marmore.py
Substitua backend_marmore.py pelo nome do arquivo do backend (por exemplo, backend_marmore (17).py).
O backend será iniciado e estará acessível em `[invalid url, do not cite]. Você pode testar os endpoints usando ferramentas como Postman, curl ou integrando com o frontend.
Configuração de Execução no PyCharm
Acesse Run > Edit Configurations.
Clique em + e selecione Python.
Configure:
Name: "Flask App"
Script path: Aponte para backend_marmore.py.
Interpreter: Use o ambiente virtual configurado.
Environment variables: Adicione FLASK_APP=backend_marmore.py.
Clique em Apply e OK.
Execute clicando em Run ou pressionando Shift + F10.
Estrutura do Projeto
A estrutura do projeto inclui:

backend_marmore.py: Arquivo principal, contendo:
Configuração do Flask com CORS para integração com frontend.
Inicialização do SQLAlchemy para conexão com MySQL.
Definição de modelos (como Marmores, Clientes, Pedidos, etc.) usando SQLAlchemy.
Rotas para CRUD (Create, Read, Update, Delete) em endpoints como /clientes, /marmores, /orcamentos, etc.
Autenticação via JWT com rotas protegidas (ex.: /login).
requirements.txt: Lista de dependências do projeto.
.env: Arquivo de variáveis de ambiente para configuração do banco de dados (não commitado no Git).
Uso
A API fornece endpoints para diversas operações, incluindo:

Autenticação: POST /login para obter um token JWT, enviando {"email": "email@example.com", "senha": "senha"}.
Clientes: CRUD em /clientes, como:
GET /clientes para listar todos os clientes.
POST /clientes para criar um cliente, enviando {"nome": "Nome", "telefone": "123456789", "email": "email@example.com"}.
PUT /clientes/<id> para atualizar, enviando o ID na URL.
DELETE /clientes/<id> para excluir.
Mármores: CRUD em /marmores, similar aos clientes, com campos como nome, preço por metro quadrado e quantidade.
Pedidos/Orcamentos: CRUD em /orcamentos, incluindo status (Pendente, Pago, Parcial).
Movimentações de Estoque: CRUD em /movimentacoes, para registrar entradas e saídas de estoque.
Estoque: Consulta em /estoque para listar itens em estoque.
Notas: Consulta em /notas para listar notas aprovadas.
Exemplo de uso com curl (com token JWT):

Listar clientes:
bash

Copiar
curl -X GET -H "Authorization: Bearer <token>" http://127.0.0.1:5000/clientes
Criar um mármore:
bash

Copiar
curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer <token>" -d '{"nome": "Mármore Branco", "preco_m2": 100.50, "quantidade": 50}' http://127.0.0.1:5000/marmores
Contribuição
Este projeto é colaborativo, com 5 membros no grupo. Para contribuir:

Clone o repositório:
bash

Copiar
git clone <URL-do-repositório>
Crie um branch para sua funcionalidade:
bash

Copiar
git checkout -b feature/nova-funcionalidade
Faça as alterações, commit e envie:
bash

Copiar
git commit -m "Descrição das alterações"
git push origin feature/nova-funcionalidade
Crie um pull request no repositório para revisão pelos colegas.
Certifique-se de atualizar o requirements.txt se adicionar novas dependências.
