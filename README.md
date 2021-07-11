# oauth2_provider_prototype
Эта штука имеет защищенную ручку для похода в неё.
Пока что она отдаёт 403, надо теперь проработать путь с токеном.

Идём вот с таким запросом:
http://127.0.0.1:8000/o/authorize/?response_type=code&client_id=hilTlueDkI9T1WdvjVu4STLgM9jMvJ7m5ginJv6K&redirect_uri=http://localhost:8000/api/hello

Жмём ОК, получаем код в УРЛе.

curl -X POST \
    -H "Cache-Control: no-cache" \
    -H "Content-Type: application/x-www-form-urlencoded" \
    "http://127.0.0.1:8000/o/token/" \
    -d "client_id=hilTlueDkI9T1WdvjVu4STLgM9jMvJ7m5ginJv6K" \
    -d "client_secret=W06fTg630ndM3xQzLlSTb3uqOzQ1diHPai2yZ2vvLfbUbMxJHFa0g3JsBnqLOtUquPyiGNcJwtpegvdNgdew91sFStRKktzxatCaulGRVaj9wmymllds1CREd39Rrrz2" \
    -d "code=EZVIoeRRWH8NdPUYimTIYF4rGFe7Vt" \
    -d "redirect_uri=http://localhost:8000/api/hello" \
    -d "grant_type=authorization_code"
    
Надо успеть это дерьмо ввести за минуту!

В ответ прилетит: 

{"access_token": "vp1nczejAARIE6I4WFKfIQJbmGHIEy", 
"expires_in": 36000, 
"token_type": "Bearer",
 "scope": "read write",
  "refresh_token": "6KsANJ8qyswv1C5yeJgJRWRAyDskj9"}


curl \
    -H "Authorization: Bearer vp1nczejAARIE6I4WFKfIQJbmGHIEy" \
    -X GET http://localhost:8000/api/hello
    
ОТДАСТ 200!!
