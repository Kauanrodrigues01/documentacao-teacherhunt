# Passo a passo para utilizar a API

- Vai no github e baixe ou faça um clone do repositório
- Com o projeto no seu PC abra ele no vscode, abra o terminal e digite **"python -m venv venv"**, depois **"venv/scripts/activate"**, depois disso tem que instalar as dependências, use o comando **"pip install -r requirements.txt"**
    ```
    python -m venv venv

    venv/scripts/activate

    pip install -r requirements.txt
    ```

- Após todas as dependências instaladas, crie o arquivo **".env"** dentro do diretório principal, **cuidado para não criar ele dentro de outra paste sem ser o diretório principal**, coloque o seguinte conteúdo dentro do arquivo **".env"**
    ```
    SECRET_KEY=-px9!&aurijpz9e*f_c8)jov!v=++5hx6r%vslywp2^l+8*@gr
    DEBUG=True
    ALLOWED_HOSTS=*
    DATABASE_URL=mysql://root@127.0.0.1:3306/teacherhunt
    # mysql://username:password@host:port/database
    ACCESS_TOKEN_LIFETIME_SECONDS = 3600
    REFRESH_TOKEN_LIFETIME_SECONDS = 7200
    ```

- Depois disso volte no terminal e execute o comando "python manage.py migrate"
- Pronto, a API está pronta para usar, para ativar o servidor use o comando "python manage.py runserver"

    ```
    python manage.py migrate

    # Iniciar o servidor
    python manage.py runserver
    ```

## Popular banco de dados(Opcional)
- Executando o arquivo populate, o banco de dados vai se preencher com vários dados aleatórios. Pode ajudar no desenvolvimento do front e mobile, pois vai ter dados para serem visualizados na aplicação. Tem que executar exatamente nessa ordem:
    ```
    python populate_subject.py
    python populate_student.py
    python populate_teacher.py
    python populate_rating.py
    python populate_favorite_teacher.py
    python populate_classroom.py
    ```

## **Aviso importante:**

- Sempre que fechar e abrir o VS Code tem que ativar a venv(ambiente virtual) antes de utilizar o "python manage.py runserver", sempre verificar se a venv está ativa antes de iniciar o servidor.
- Quando a venv está ativa fica o nome (venv) em cima da linha principal do terminal

## Qualquer erro tenta pesquisar no chatgpt
