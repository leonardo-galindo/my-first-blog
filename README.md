# Django 
Todos os comandos realizado no CMD/Terminal, precisa ser executado na **VIRTUALENV**

**Ambiente virtual**
1. Criar uma pasta para o projeto
2. Acessar a pasta via terminal
3. Executar o comando: 
    3.1 Linux: *python3 -m venv myvenv*
    3.2 Windows *python -m venv myvenv*

**Ativando a VM**
1. Abrir o terminal
    1.1 Linux: *source myvenv/bin/activate*
    1.2 Windows: *myvenv\Scripts\activate*

**Atualizando pip na venv**
*python -m pip install --upgrade pip*

# Instalando pacotes com requisitos

O arquivo "requirements.txt" guarda as depenências que serão instaladas utilizando o pip install:

Primeiro, crie um arquivo requirements.txt dentro da sua pasta djangogirls/ usando o editor de código que você instalou mais cedo. Para fazer isso, abra um novo arquivo no editor e salve-o como requirements.txt na pasta djangogirls.

E adicione o seguinte texto ao arquivo djangogirls/requirements.txt:
*Django==3.1.2*

**Instalando Django**
*pip install -r requirements.txt*

**Criando um projeto**
Linux: *django-admin startproject mysite .*
Windows: *django-admin.exe startproject mysite .*

OBS: *O ponto . é crucial por que ele diz para o script instalar o Django no diretório atual (o ponto . é um atalho para referenciar este diretório).*

# Mudando as configurações
**No arquivo: settings.py - alterar**
TIME_ZONE = 'America/Sao_Paulo'
LANGUAGE_CODE = 'pt-BR'
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')

# Observação
Quando DEBUG for True e ALLOWED_HOSTS estiver vazia, o domínio do site será validado como ['localhost', '127.0.0.1', '[::1]']. Isso não corresponderá ao nosso domínio no PythonAnywhere quando implantarmos a nossa aplicação, então vamos mudar a seguinte configuração: ALLOWED_HOSTS = *['127.0.0.1', '.pythonanywhere.com']*

**Configurando um banco de dados**
Para criar um banco de dados para o nosso blog, vamos executar o seguinte comando no console. Digite: *python manage.py migrate* (precisamos estar no diretório que contém o arquivo manage.py

**Iniciando o servidor web**
Você precisa estar no diretório que contém o arquivo **manage.py**
*python manage.py runserver*

# Navegador 
http://127.0.0.1:8000/

**Criando uma aplicação**
Para manter tudo arrumado, vamos criar uma aplicação separada dentro do nosso projeto. É muito bom ter tudo organizado desde o início. Para criar uma aplicação, precisamos executar o seguinte comando:
Windows/Linux: *python manage.py startapp blog*

Depois de criar uma aplicação, também precisamos dizer ao Django que ele deve usá-la. Fazemos isso no arquivo mysite/settings.py -- abra-o no seu editor de código. Precisamos encontrar o INSTALLED_APPS e adicionar uma linha com 'blog', logo acima do ]. O resultado final ficará assim:

**mysite/settings.py**

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',
]

**Criando um modelo de postagem para o nosso blog**
[Django Girls](https://tutorial.djangogirls.org/pt/django_models/)
No arquivo *blog/models.py* definimos todos os objetos chamados Modelos -- este é um lugar em que vamos definir nossa postagem do blog.
**blog/models.py**
from django.conf import settings
from django.db import models
from django.utils import timezone

**Criando tabelas para nossos modelos no banco de dados**
O último passo é adicionar nosso novo modelo ao banco de dados. Primeiramente, precisamos fazer com que o Django entenda que fizemos algumas alterações nos nossos modelos.
Windows/Linux: *python manage.py makemigrations blog*

O Django preparou um arquivo de migração que precisamos aplicar ao nosso banco de dados.
Windows/Linux: *python manage.py migrate blog*

**Django Admin**
[Django Girls](https://tutorial.djangogirls.org/pt/django_admin/)
Para adicionar, editar e deletar os posts que acabamos de modelar, nós usaremos o admin do Django.
**blog/admin.py**
from django.contrib import admin
from .models import Post

admin.site.register(Post)

*criar um superusuário (superuser) - uma conta de usuário que pode controlar tudo no site.*

Windows/Linux: *python manage.py createsuperuser*

# Dados do super user
lgalindo
django8264

**DEPLOY**
[Deploy](https://tutorial.djangogirls.org/pt/deploy/)
Instalação:
Windows: [Git](https://git-scm.com/)
Ubuntu: *sudo apt install git*

**Github**
git remote add origin https://github.com/leonardo-galindo/my-first-blog.git
git branch -M main
git push -u origin main