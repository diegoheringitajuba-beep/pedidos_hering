# Projeto Hering Franchise

Este projeto é uma aplicação Flask para gestão e acompanhamento de pedidos, com suporte a importação de dados via Excel e armazenamento em SQLite.

## Como rodar localmente

1. Crie um ambiente virtual:
   ```bash
   python -m venv venv
   ```

2. Ative o ambiente virtual:
   - Windows: `venv\Scripts\activate`
   - Linux/Mac: `source venv/bin/activate`

3. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

4. Execute a aplicação:
   ```bash
   python app.py
   ```

## Deploy no Render

Para fazer o deploy no Render:

1. Crie um novo **Web Service** no Render.
2. Conecte seu repositório do GitHub.
3. Configure os seguintes campos:
   - **Runtime**: `Python 3`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app`
4. (Opcional) Adicione uma variável de ambiente `SECRET_KEY` para maior segurança.

**Nota sobre SQLite no Render:**
O sistema de arquivos do Render é efêmero por padrão. Para que os dados do SQLite persistam entre deploys e reinicializações, você deve:
1. Ir em **Dashboard > Seu Serviço > Disks**.
2. Criar um novo disco (ex: 1GB).
3. Definir o **Mount Path** como `/data`.
4. Adicionar uma variável de ambiente `DATABASE_URL` com o valor `sqlite:////data/hering_db.sqlite`.
