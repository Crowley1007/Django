# 📘Curso de Django (Python)

## 🔹 Aula 3 – Criação e Estrutura do Projeto em Django

## 📍 Pré-requisitos

### 1. Instalação do Django

1.1 Com o ambiente virtual ativo, instale o Django:
- pip install django

1.2 Verifique se foi instalado corretamente:
- django-admin --version

### 2. Criação do Primeiro Projeto Django

2.1 Crie o projeto inicial:
- django-admin startproject meu_projeto .

2.2 Estrutura do Projeto:

    meu_projeto/
    ├── manage.py
    └── meu_projeto/
        ├── __init__.py
        ├── settings.py
        ├── urls.py
        ├── asgi.py
        └── wsgi.py

- **manage.py**

    É um utilitário de linha de comando para interagir com o projeto.
    
    Permite rodar comandos do Django:

- **__init__.py**
  
  Indica ao Python que esta pasta é um pacote.

  Geralmente fica vazio, mas permite inicializações.

- **settings.py** 

    Arquivo mais importante para configurações.
    
    Contém:
    
    Configuração do banco de dados.
    
    Lista de apps instalados (INSTALLED_APPS).
    
    Configuração de idioma e fuso horário.
    
    Configurações de templates, middlewares e autenticação.

- **urls.py** 

    Define o roteamento de URLs da aplicação.
    
    Quando o usuário acessa uma rota, o Django procura a view correspondente aqui.
    
    📍 Exemplo:

    
        from django.contrib import admin
        from django.urls import path
        
        urlpatterns = [
            path('admin/', admin.site.urls),
        ]
                
        Aqui temos a rota /admin, que abre o painel administrativo do Django.

- **wsgi.py / asgi.py**
   
    WSGI (Web Server Gateway Interface): usado por servidores web tradicionais (Apache, Gunicorn).
    
    ASGI (Asynchronous Server Gateway Interface): suporta aplicações assíncronas (WebSockets, tempo real).
    
    Normalmente, não alteramos esses arquivos manualmente.

### 3. Rodando o Servidor de Desenvolvimento

3.1 Entre na pasta do projeto e rode o servidor:v
- python manage.py runserver

3.2 A saída será algo como:
- Starting development server at http://127.0.0.1:8000/

👉 Abra no navegador: http://127.0.0.1:8000

Você verá a página inicial do Django, confirmando que o ambiente está pronto. 

Para parar o servidor pressione Ctrl + C no terminal.

### 4. Criação e Estrutura de um App no Django
Além do projeto, o Django organiza funcionalidades em apps.

4.1 Criando um app:
- python manage.py startapp blog

4.2 Estrutura gerada:

    blog/
    ├── admin.py
    ├── apps.py
    ├── migrations/
    ├── models.py
    ├── tests.py
    └── views.py

models.py → Define tabelas e relacionamentos (ORM).

views.py → Funções ou classes que processam requisições.

admin.py → Configuração para aparecer no painel administrativo.

migrations/ → Alterações do banco de dados.

apps.py → Configurações internas do app.


4.3 Registrando o App no Projeto

Após criar o app, precisamos registrá-lo no projeto.

No arquivo meu_projeto/settings.py, adicione em INSTALLED_APPS:


    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'blog',  # app criado
    ]

### 5. Criando uma View Simples no App

No arquivo blog/views.py:

    from django.http import HttpResponse
    def home(request):
        return HttpResponse("<h1>Bem-vindo ao Blog!</h1>")

###  6. Configurando URLs do App

5.1 Crie o arquivo blog/urls.py:

    from django.urls import path
    from . import views
    
    urlpatterns = [
        path('', views.home, name='home'),
    ]

5.2 Agora, conecte o urls.py do app ao urls.py do projeto.

No arquivo meu_projeto/urls.py:

    from django.contrib import admin
    from django.urls import path, include
    
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('blog/', include('blog.urls')),  # rota do app blog
    ]
    

###  7. Testando no Navegador

7.1 Execute o servidor:

    python manage.py runserver

7.2 Acesse no navegador:

    http://127.0.0.1:8000/blog/

👉 Você verá a mensagem:

  "Bem-vindo ao Blog!"



Para finalizar esta aula, como adicionamos do Django no projeto, 
vamos incluir as dependências no arquivo requirements.txt

No terminal digite :

    pip freeze > requirements.txt

### Cronograma das Aulas 

| Aula	                                                 | Branch  |                                                 Clique no Link |
|:------------------------------------------------------|:-------:|---------------------------------------------------------------:|
| Aula 1 – O que é Django?                              | aula_1  |              [Link](https://github.com/SANDEISON/curso_django) |
| Aula 2 - Configuração do Ambiente Django              | aula_2  |  [Link](https://github.com/SANDEISON/curso_django/tree/aula_2) |
| Aula 3 - Criação e Estrutura do Projeto em Django     | aula_3  |  [Link](https://github.com/SANDEISON/curso_django/tree/aula_3) |
| Aula 4 - Templates no Django                          | aula_4  |  [Link](https://github.com/SANDEISON/curso_django/tree/aula_4) |
| Aula 5 - Models e Banco de Dados no Django (ORM)      | aula_5  |  [Link](https://github.com/SANDEISON/curso_django/tree/aula_5) |
| Aula 6 - Exibindo dados do Models no Template         | aula_6  |  [Link](https://github.com/SANDEISON/curso_django/tree/aula_6) |
| Aula 7 - Enviando dados do Template para a view       | aula_7  |  [Link](https://github.com/SANDEISON/curso_django/tree/aula_7) |
| Aula 8 - Relacionamentos no Django                    | aula_8  |  [Link](https://github.com/SANDEISON/curso_django/tree/aula_8) |
| Aula 9 - Explorando o Painel Administrativo do Django | aula_9  |  [Link](https://github.com/SANDEISON/curso_django/tree/aula_9) |
| Aula 10 - Views Baseadas em Função (FBV)              | aula_10 | [Link](https://github.com/SANDEISON/curso_django/tree/aula_10) |
| Aula 11 - Views Baseadas em Classe (CBV)              | aula_11 | [Link](https://github.com/SANDEISON/curso_django/tree/aula_11) |








