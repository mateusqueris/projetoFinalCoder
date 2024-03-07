
# Proposta do Projeto:

Projeto Final de conclusão do curso de Python da plataforma CoderHouse. Turma 54375
Trabalho em equipe pelos alunos: Mateus Queris, Nathalia Bertos e Nicole Moraes Graniço.

Exercicio 1: Escolher um API da lista disponível, Fazer extração de 3 tabelas, Estar disponível no GITHub.
Exercicio 2: Realizar o tratamento das bases coletadas via API do projeto final. Ajustar colunas e linhas, filtros de linhas e colunas, unstack/stack, tratamento do tipo das variáveis, ajuste de missing e tratamento de colunas string.
Exercicio 3: Criar um Virtual Environment e um arquivo README.

Projeto Python que integra dados sobre bancos e unidades federativas do Brasil de APIs públicas.

## Bibliotecas Necessárias:

- Bibliotecas Python: requests, pandas, sqlite3, plyer
        
        -> pip install requests
        -> pip install pandas
        -> pip install sqlite3
        -> pip install plyer
## API Escolhida

API escolhida:
    BRASIL API(1.0.0)
        Link documentação Brasil API:
        https://brasilapi.com.br/docs
        
        Bancos:
        -> https://brasilapi.com.br/api/banks/v1 

        Cidade:
        -> https://brasilapi.com.br/api/cptec/v1/cidade

        Siglas Estados:
        -> https://brasilapi.com.br/api/ibge/uf/v1 


## Tratamento e manipulação dos dados:
    
    
    Renomeação de colunas:
        # Renomeia as colunas do DataFrame
        df.rename(columns={'ispb': 'ISPB', 'name': 'Nome', 'code': 'Código', 'fullName': 'Nome Banco'}, inplace=True)

    Conversão de tipos de dados
        df['Código'] = df['Código'].astype('Int64')

    Preenchimento de valores ausentes
        df.fillna({'Código': 0, 'Nome Banco': 'Sem nome'}, inplace=True)

    Transformações de strings
        # Transforma todos os valores na coluna 'Nome' em maiúsculas
        df['Nome'] = df['Nome'].str.upper()

        # Transforma a primeira letra de cada palavra na coluna 'Nome Banco' em maiúscula
        df['Nome Banco'] = df['Nome Banco'].str.title()

    Armazenamento dos dados em bancos de dados SQLite
        # Salva o DataFrame no SQLite
        df.to_sql('df', conn, if_exists='replace', index=False)

    Notificação de sucesso ou falha na extração e tratamento dos dados

        # Alerta de sucesso
        notification.notify(
            title='sucesso',
            message='Base de dados carregada com sucesso',
            app_name='Alerta',
            timeout=10
        )
        # Alerta de erro
        notification.notify(
            title='erro',
            message='Falha no carregamento da base de dados',
            app_name='Alerta',
            timeout=10
        )

## Github

para publicar o projeto no github é necessário o download da aplicação GIT 
link para download:
    https://gitforwindows.org/

Comandos para configuração do GIT:
    
    Abrir CMD no Windows.

    Primeiro Comando para verificar se o Git está instalado corretamente: 
        GIT

    Segundo Comando para criar usuario:  
        git config --global user.name "seu nome de usuário"

    Terceiro Comando para vincular e-mail:  
        git config --global user.email "seuemail@gmail.com"
    
    Quarto comando para validar configuração:  
        git config --list

    Necessario Reiniciar Computador.
   
Comandos para subir projeto no Github 

    Abrir Terminal no Vscode
    git init
    git status
    git add temp.txt ou git add .
    git commit –m “coloque sua mensagem aqui”

    Acessar Github: 
    https://github.com/

    Criar um novo Repositorio

    Utilizar a opção: …or push an existing repository from the command line
        git remote add origin https://github.com/mateusqueris/projetoFinalCoder.git
        git branch -M main
        git push -u origin main

## Virtual Environment

    Criar ambiente:
        -> virtualenv nome_do_ambiente


    Navegar pasta projeto
        -> cd projeto_final-main

    Ativar ambiente virtual 
        -> .\myenv\Scripts\Activate.ps1

    Verificar se ambiente virtual está ativado:
        -> Get-Command python

    Exemplo de instalação de biblioteca no Virtual Environment:
        -> & "$env:VIRTUAL_ENV\Scripts\pip.exe" install pandas

## Banco de dados


O projeto utiliza o banco de dados SQLite dentro do ambiente do VSCode para armazenar os dados obtidos da API Brasil. 
Os dados são transformados em dataframes e, em seguida, inseridos no banco de dados utilizando a função to_sql.

Operações Realizadas:

Os dados são transformados em dataframes e salvos no banco de dados SQLite utilizando a função to_sql.

EX: df2.to_sql('df2', conn, if_exists='replace', index=False)

A conexão com o arquivo projetofinal.db é estabelecida utilizando o módulo sqlite3.
Extensão Utilizada:

Para visualização e interação com o banco de dados SQLite dentro do VSCode, é recomendada a utilização da extensão "SQLITE3 Editor". 
