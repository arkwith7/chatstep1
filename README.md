# 1. 장고 프로젝트 생성
## 1.1. 장고 프로젝트를 실행할 디렉토리로 이동합니다.
```
(chat_env) C:\Users\saint\GroupProject>cd step1
```

## 1.2 장고 프로젝트를 django-admin startproject "프로젝트명" 으로 생성
```
(chat_env) C:\Users\saint\GroupProject\step1>django-admin startproject mychatsite

(chat_env) C:\Users\saint\GroupProject\step1>dir/w
 C 드라이브의 볼륨에는 이름이 없습니다.
 볼륨 일련 번호: EA5F-25B4

 C:\Users\saint\GroupProject\step1 디렉터리

[.]          [..]         [mychatsite]
               0개 파일                   0 바이트
               3개 디렉터리  264,312,532,992 바이트 남음
```

## 1.3 생성된 프로젝트 디렉토리로 이동
```
(chat_env) C:\Users\saint\GroupProject\step1>
(chat_env) C:\Users\saint\GroupProject\step1>cd mychatsite

(chat_env) C:\Users\saint\GroupProject\step1\mychatsite>
(chat_env) C:\Users\saint\GroupProject\step1\mychatsite>dir/w
 C 드라이브의 볼륨에는 이름이 없습니다.
 볼륨 일련 번호: EA5F-25B4

 C:\Users\saint\GroupProject\step1\mychatsite 디렉터리

[.]          [..]         manage.py    [mychatsite]
               1개 파일                 557 바이트
               3개 디렉터리  264,312,532,992 바이트 남음
```
## 1.4 생성된 프로젝트 실행
```
(chat_env) C:\Users\saint\GroupProject\step1\mychatsite>
(chat_env) C:\Users\saint\GroupProject\step1\mychatsite>
(chat_env) C:\Users\saint\GroupProject\step1\mychatsite>python manage.py runserver
Performing system checks...

System check identified no issues (0 silenced).

You have 14 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.
September 09, 2020 - 13:50:54
Django version 2.0.2, using settings 'mychatsite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
[09/Sep/2020 13:51:07] "GET / HTTP/1.1" 200 16348
[09/Sep/2020 13:51:07] "GET /static/admin/css/fonts.css HTTP/1.1" 200 423
[09/Sep/2020 13:51:07] "GET /static/admin/fonts/Roboto-Regular-webfont.woff HTTP/1.1" 200 80304
[09/Sep/2020 13:51:07] "GET /static/admin/fonts/Roboto-Bold-webfont.woff HTTP/1.1" 200 82564
[09/Sep/2020 13:51:07] "GET /static/admin/fonts/Roboto-Light-webfont.woff HTTP/1.1" 200 81348
```
# 2. 장고 어플리케이션(App) 생성
```
(chat_env) C:\Users\saint\GroupProject\step1\mychatsite>python manage.py startapp chatapp

(chat_env) C:\Users\saint\GroupProject\step1\mychatsite>dir/w
 C 드라이브의 볼륨에는 이름이 없습니다.
 볼륨 일련 번호: EA5F-25B4

 C:\Users\saint\GroupProject\step1\mychatsite 디렉터리

[.]          [..]         [chatapp]    db.sqlite3   manage.py    [mychatsite]
               2개 파일                 557 바이트
               4개 디렉터리  264,305,500,160 바이트 남음
```
## 2.1 장고 어플리케이션(App)에서 views.py파일에 페이지 등록
**views.py**
```
from django.http import HttpResponse

# Create your views here.
 
def index(request):
    return HttpResponse("<h1>Hello, World!</h1>")
```

# 3. 프로젝트에 어플리케이션(App) 연결
## 3.1 settings.py에 어플리케이션(App) 등록
**settings.py**
```
......
...............
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
#  여기에 생성한 chatapp 어플리케이션 이름 등재
    'chatapp',
]
.............
................
```

# 3.2 urls.py에 어플리케이션(App)의 views.py function 등록
**urls.py**
=======================================
```
from django.contrib import admin
from django.urls import path
# 어플리케이션(App)의 views.py 임포트
from chatapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
# 어플리케이션(App)의 views.py function 추가
    path('', views.index),
]
```
=======================================
