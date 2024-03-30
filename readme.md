## Django is a ready-to-use sample project on Beget.ru.
### You just need to upload these files into `public_html` folder and change the necessary parts.

#### After you upload these files to Beget hosting, you need to make a couple of changes.

1. Download the virtual environment (venv) from here and load it into `public_html`: https://cloud.mail.ru/public/9BjJ/EHUvSLQz7
2. Modify this code -> `.htaccess`:
```
PassengerEnabled On
PassengerAppRoot /home/your_letter/your_username/your_domain/public_html/django_project/django_project
PassengerPython /home/your_letter/your_username/your_domain/public_html/venv/bin/python
```
3. After modify this code -> `~\beget_django_example\django_project\django_project\passenger.py`:
```
import os, sys
site_user_root_dir = '/home/your_letter/your_username/your_domain/public_html'
sys.path.insert(0, site_user_root_dir + '/django_project')
sys.path.insert(1, site_user_root_dir + '/venv/lib/python3.11/site-packages')
os.environ['DJANGO_SETTINGS_MODULE'] = 'django_project.settings'
from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()
```
4. Finally, modify this code -> ``:
 ```
from pathlib import Path
import os

BASE_DIR = Path(__file__).resolve().parent.parent

SECRET_KEY = 'your_secret_key'                              # <----
DEBUG = True
ALLOWED_HOSTS = ['your_domain', '127.0.0.1', 'localhost']   # <----

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'django_app'
]
 ```

#### Versions:
- Django==4.2.6
- whitenoise==6.6.0    <---- This library is for static files to run on the server

## That's it. Everything works...
#### If you have any problems, you can write on Telegram: https://t.me/ozodbek_sobirjonovich
