# Ex.06 Book Front Cover Page Design
# Date: 28/10/2024
# AIM:
To design a book front cover page using HTML and CSS.

# DESIGN STEPS:
## Step 1:
Create a Django Admin project.

## Step 2:
Create an app in the Django interface.

## Step 3:
Create a folder named 'static' in the app folder.

## Step 4:
Create a new HTML file in the static folder.

## Step 5:
Write the HTML code with relevant CSS properties.

## Step 6:
Choose the appropriate style and color scheme.

## Step 7:
Insert the images in their appropriate places.

## Step 8:
Publish the website in the LocalHost.

# PROGRAM:

# index.html:

    {% load static %}
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Book Cover</title>
        <style>
            body {
                font-family: 'Brush Script MT', cursive;
                margin: 0;
                padding: 0;
                display: flex;
                justify-content: center;
                align-items: center;
                height: 100vh;
                background: linear-gradient(to bottom, #f8e2d2, #f4d7c3);
            }

            .cover {
                width: 300px;
                height: 500px;
                background: url("{% static 'images/image.jpg' %}") no-repeat center center;
                background-size: cover;
                display: flex;
                flex-direction: column;
                justify-content: space-between;
                padding: 20px;
                box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.5);
                color: white;
                text-align: center;
                border: 5px solid rgba(255, 255, 255, 0.8);
                position: relative;
            }

            .cover h1 {
                font-size: 40px;
                font-weight: bold;
                color: white; 
                text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
            }

            .cover p {
                font-size: 25px;
                color: white; 
                text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.7);
            }

            .cover .author {
                font-size: 20px;
                font-style: italic;
                margin-top: 20px;
                color: white;
                position: relative; 
            }

            .cover .image-container {
                position: absolute;
                top: 70%;
                left: 50%;
                transform: translate(-50%, -50%);
                width: 80px;
                height: 80px;
                border-radius: 50%;
                overflow: hidden;
                border: 3px solid rgba(255, 255, 255, 0.8);
                box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.5);
            }

            .cover .image-container img {
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        </style>
    </head>
    <body>
        <div class="cover">
            <h1>Adventures in Web Security</h1>
            <p>A Journey into the World of Ethical Hacking</p>
            <div class="author">By Jaiyantan</div>
            <div class="image-container">
                <img src="{% static 'images/photo.jpeg' %}" alt="Author Image">
            </div>
            <div class="footer">Saveetha Engineering College Press</div>
        </div>
    </body>
    </html>

# views.py:

    from django.shortcuts import render

    def book_cover(request):
        return render(request, 'index.html', {
            'title': 'Adventures in Web Security',
            'subtitle': 'A Journey into the World of Ethical Hacking',
            'author': 'By Jaiyantan',
            'publisher': 'Saveetha Engineering College Press',
            'cover_image': 'static/images/image.jpg',
            'author_image': 'static/images/photo.jpeg',
        })

# settings.py:

    from pathlib import Path

    # Build paths inside the project like this: BASE_DIR / 'subdir'.
    BASE_DIR = Path(__file__).resolve().parent.parent


    # Quick-start development settings - unsuitable for production
    # See https://docs.djangoproject.com/en/5.1/howto/deployment/checklist/

    # SECURITY WARNING: keep the secret key used in production secret!
    SECRET_KEY = 'django-insecure-hfei$gl-l*7jmj4p$#wns@7z=k0l2^r!rf6+(x8qi)j+(9r$9i'

    # SECURITY WARNING: don't run with debug turned on in production!
    DEBUG = True

    ALLOWED_HOSTS = []


    # Application definition

    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        'bookapp',
    ]

    MIDDLEWARE = [
        'django.middleware.security.SecurityMiddleware',
        'django.contrib.sessions.middleware.SessionMiddleware',
        'django.middleware.common.CommonMiddleware',
        'django.middleware.csrf.CsrfViewMiddleware',
        'django.contrib.auth.middleware.AuthenticationMiddleware',
        'django.contrib.messages.middleware.MessageMiddleware',
        'django.middleware.clickjacking.XFrameOptionsMiddleware',
    ]

    ROOT_URLCONF = 'bookproject.urls'

    TEMPLATES = [
        {
            'BACKEND': 'django.template.backends.django.DjangoTemplates',
            'DIRS': [],
            'APP_DIRS': True,
            'OPTIONS': {
                'context_processors': [
                    'django.template.context_processors.debug',
                    'django.template.context_processors.request',
                    'django.contrib.auth.context_processors.auth',
                    'django.contrib.messages.context_processors.messages',
                ],
            },
        },
    ]

    WSGI_APPLICATION = 'bookproject.wsgi.application'


    # Database
    # https://docs.djangoproject.com/en/5.1/ref/settings/#databases

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.sqlite3',
            'NAME': BASE_DIR / 'db.sqlite3',
        }
    }


    # Password validation
    # https://docs.djangoproject.com/en/5.1/ref/settings/#auth-password-validators

    AUTH_PASSWORD_VALIDATORS = [
        {
            'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
        },
        {
            'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
        },
        {
            'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
        },
        {
            'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
        },
    ]


    # Internationalization
    # https://docs.djangoproject.com/en/5.1/topics/i18n/

    LANGUAGE_CODE = 'en-us'

    TIME_ZONE = 'UTC'

    USE_I18N = True

    USE_TZ = True


    # Static files (CSS, JavaScript, Images)
    # https://docs.djangoproject.com/en/5.1/howto/static-files/

    STATIC_URL = '/static/'

    # Default primary key field type
    # https://docs.djangoproject.com/en/5.1/ref/settings/#default-auto-field

    DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

# OUTPUT:

!['Result pic'](image.png)

# RESULT:
The program for designing book front cover page using HTML and CSS is completed successfully.
