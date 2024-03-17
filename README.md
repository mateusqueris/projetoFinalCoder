# Projeto Final Python CoderHouse 🐍

Projeto Final de conclusão do curso de Python da plataforma CoderHouse. 
Alunos: Mateus Queris, Nathalia Bertos e Nicole Moraes Graniço.
Este projeto foi desenvolvido como parte do curso de Python da CoderHouse, Turma 54375. 🎓

## Descrição do Projeto 🚀

O projeto consiste em um sistema Python que integra dados sobre bancos e unidades federativas do Brasil de APIs públicas. Realizado como exercício final do curso de Python da CoderHouse.

## Funcionalidades 🛠️

1. Extração de dados de APIs públicas.
2. Tratamento e manipulação dos dados coletados.
3. Armazenamento dos dados em banco de dados SQLite.
4. Notificação de sucesso ou falha na extração e tratamento dos dados.

## Bibliotecas Necessárias 📚

- requests
- pandas
- sqlite3
- plyer

Instalação:

- pip install requests
- pip install pandas
- pip install sqlite3
- pip install plyer

## Documentação Brasil API (1.0.0) 🌐

 Endpoints utilizados:
 Bancos: https://brasilapi.com.br/api/banks/v1
 Cidade: https://brasilapi.com.br/api/cptec/v1/cidade
 Siglas Estados: https://brasilapi.com.br/api/ibge/uf/v1

## Tratamento e Manipulação dos Dados 🛠️
Exemplo de Tratamento:

Renomeando de colunas:
- df.rename(columns={'ispb': 'ISPB', 'name': 'Nome', 'code': 'Código', 'fullName': 'Nome Banco'}, inplace=True)

Covertendo tipos de dados:
- df['Código'] = df['Código'].astype('Int64')

Melhorando valores ausentes:
- df.fillna({'Código': 0, 'Nome Banco': 'Sem nome'}, inplace=True)

Transformações de strings:
- df['Nome'] = df['Nome'].str.upper()
- df['Nome Banco'] = df['Nome Banco'].str.title()

Armazenamento dos dados em bancos de dados SQLite:
- df.to_sql('df', conn, if_exists='replace', index=False)

## Ambiente Virtual 🌐

Criar ambiente:

- virtualenv nome_do_ambiente

Ativar ambiente virtual:

- .\nome_do_ambiente\Scripts\Activate.ps1

Verificar se o ambiente está ativado:
- Get-Command python

## Banco de Dados 🗃️

O projeto utiliza o banco de dados SQLite para armazenar os dados obtidos das APIs públicas do Brasil. Após a extração e o tratamento dos dados, eles são transformados em DataFrames e, em seguida, salvos no banco de dados SQLite utilizando a função to_sql do pandas.

### Operações Realizadas:

- Transformação dos dados em DataFrames.
- Salvamento dos dados no banco de dados SQLite utilizando a função to_sql do pandas.

### Extensão Utilizada:

- A extensão "SQLite3 Editor" no VSCode foi utilizada para visualizar e gerenciar o banco de dados SQLite.


