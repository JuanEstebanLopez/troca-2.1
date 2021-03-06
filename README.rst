=====
Troca
=====

Troca is a web platform designed to support the creation and implementation of 
cultural projects, which facilitates the dissemination, exchange and donation of skills
or knowledge among members of the virtual community.

Troca es una plataforma web diseñada para apoyar la creación y ejecución de proyectos
culturales, la cual facilita la divulgación, el intercambio y la donación de habilidades
o conocimientos entre los miembros de la comunidad virtual.

Quick start
-----------

1. Add in the setting.py::

    ###########
    ##Agregar##
    from django.conf.global_settings import TEMPLATE_CONTEXT_PROCESSORS
    ###########

    ###########
    ##Agregar##
    SETTINGS_DIR = os.path.dirname(__file__)
    PROJECT_PATH = os.path.join(SETTINGS_DIR, os.pardir)
    PROJECT_PATH = os.path.abspath(PROJECT_PATH)
    LOGIN_URL = '/login/'
    ###########


    INSTALLED_APPS = (
    ...
    ###########
    ##Agregar##
    'troca',
	'registration',
	'crispy_forms',
	'crispy_forms_foundation',
	'ajax_select',
	'pure_pagination',
	'froala_editor',
	'phileo',
	'django_social_share',
	'sanitizer',
	'django.contrib.humanize',
    ###########
    )
    
    ###########
    ##Agregar##
    AUTHENTICATION_BACKENDS = ('phileo.auth_backends.CanLikeBackend',)
    EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
    EMAIL_USE_TLS = True
    EMAIL_HOST = 'smtp.gmail.com'
    EMAIL_PORT = 587
    DEFAULT_FROM_EMAIL = 'comunlaboratorio@gmail.com'
    EMAIL_HOST_USER = 'comunlaboratorio@gmail.com'
    EMAIL_HOST_PASSWORD = 'comunlab2014'
    PHILEO_LIKABLE_MODELS = {
        'Project': {},  
        'UserProfile': {},
        'Comment': {},
    }
    ###########
    
    ###########
    ##Agregar##
    TEMPLATE_CONTEXT_PROCESSORS += (
        'django.core.context_processors.request',
        #'django_messages.context_processors.inbox',
    )
    PAGINATION_SETTINGS = {
        'PAGE_RANGE_DISPLAYED': 9,
        'MARGIN_PAGES_DISPLAYED': 2,
    }
    ###########
    
    ###########
    ##Agregar##
    MEDIA_ROOT= os.path.join(PROJECT_PATH, 'media')
    MEDIA_URL='/media/'
    FROALA_UPLOAD_PATH='/media/uploads/froala_editor/images/'
    #Template context processors
    ("django.contrib.auth.context_processors.auth",
    "django.core.context_processors.debug",
    "django.core.context_processors.i18n",
    "django.core.context_processors.media",
    "django.core.context_processors.static",
    "django.core.context_processors.tz",
    "django.contrib.messages.context_processors.messages",
    "postman.context_processors.inbox")
    #Forms template
    SANITIZER_ALLOWED_TAGS = ['a', 'p', 'img', 'strong', 'em', 'u', 'blockquote', 'pre', 'h1', 'h2', 'h3', 'h4', 'h5', 'h6']
    SANITIZER_ALLOWED_ATTRIBUTES = ['href', 'src']
    CRISPY_TEMPLATE_PACK = 'foundation-5'
    ('django.contrib.auth.backends.ModelBackend',)
    ###########

2. Include the polls URLconf in your project urls.py like this::

  url(r'^', include('troca.urls')),

3. Run `python manage.py migrate` to create the troca models.

4. Run `python manage.py createsuperuser` to create a super user.

5. Start the development server and visit http://127.0.0.1:8000/.

6. Visit http://127.0.0.1:8000/admin/ and create a Skill_Categories and Skills whith the super user.

7. Visit http://127.0.0.1:8000 to participate in troca.
