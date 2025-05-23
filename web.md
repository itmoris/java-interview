[Вопросы для собеседования](README.md)

# Основы Web
+ [Что такое _WWW_?](#что-такое-www)
+ [Что такое _W3C_?](#что-такое-w3c)
+ [Что такое _HTTP_ и _HTTPS_? Чем они отличаются?](#что-такое-http-и-https-чем-они-отличаются)
+ [Чем отличаются методы HTTP/1.1 и HTTP/2?](#чем-отличаются-методы-http11-и-http2)
+ [Какие серии кодов состояния есть в HTTP?](#какие-серии-кодов-состояния-есть-в-http)
+ [Чем отличаются методы _GET_ и _POST_?](#чем-отличаются-методы-get-и-post)
+ [Чем отличаются методы _POST_, _PUT_ и _PATCH_?](#чем-отличаются-методы-post-put-и-patch)
+ [Что такое _MIME тип_?](#что-такое-mime-тип)
+ [Что такое _Web service_?](#что-такое-web-service)
+ [Что такое _Web server_?](#что-такое-web-server)
+ [Что такое _Web application_?](#что-такое-web-application)
+ [Что такое _Application server_?](#что-такое-application-server)
+ [Чем отличаются _Web server_ и _Application server_?](#чем-отличаются-web-server-и-application-server)
+ [Что такое _WebSocket_?](#что-такое-websocket)
+ [Что такое _cookies_?](#что-такое-cookies)
+ [Что такое _«сессия»_?](#что-такое-сессия)

## Что такое _WWW_?

__WWW, World Wide Web (Всемирная паутина)__ — распределённая система, предоставляющая доступ к связанным между собой документам, расположенным на различных компьютерах, подключённых к Интернету. Для обозначения этого термина также используют слово _web_.

[к оглавлению](#Основы-web)

## Что такое _W3C_?

__W3C, World Wide Web Consortium (Консорциум Всемирной паутины)__ — организация, разрабатывающая и внедряющая технологические стандарты для WWW.

W3C разрабатывает для Интернета единые принципы и стандарты, называемые _«рекомендациями» (W3C Recommendations)_, которые затем внедряются производителями программ и оборудования. Таким образом достигается совместимость между программными продуктами и аппаратурой различных компаний.

[к оглавлению](#Основы-web)

## Что такое _HTTP_ и _HTTPS_? Чем они отличаются?

__HTTP, HyperText Transfer Protocol (Протокол передачи гипертекста)__ — протокол прикладного уровня передачи данных.

Основой HTTP является технология «клиент-сервер»:

+ _Потребители (клиенты)_, которые инициируют соединение и посылают запрос;
+ _Поставщики (серверы)_, которые ожидают соединения для получения запроса, производят необходимые действия и возвращают обратно сообщение с результатом.

Для идентификации ресурсов HTTP использует глобальные URI.

HTTP не сохраняет своего состояния. Это означает отсутствие сохранения промежуточного состояния между парами «запрос-ответ».

Структура протокола:

1. _Стартовая строка (starting line)_ — определяет тип сообщения;
2. _Заголовки (headers)_ — характеризуют тело сообщения, параметры передачи и прочие сведения;
3. _Тело сообщения (message body)_ — непосредственно данные сообщения. Обязательно должно отделяться от заголовков пустой строкой.

Заголовки и тело сообщения могут отсутствовать, но стартовая строка является обязательным элементом, так как указывает на тип запроса/ответа.

__HTTPS, HyperText Transfer Protocol Secure__ — расширение протокола HTTP, поддерживающее шифрование. Данные, передаваемые по протоколу HTTPS, «упаковываются» в криптографический протокол SSL или TLS, что обеспечивает защиту от атак, основанных на прослушивании сетевого соединения (при условии, что будут использоваться шифрующие средства и сертификат сервера проверен и ему доверяют).

__Различия _HTTP_ и _HTTPS___:

+ HTTPS является расширением HTTP.

+ HTTP использует не зашифрованное соединение. Соединение по HTTPS поддерживает шифрование.

+ Работа по HTTP быстрей и менее ресурсоёмко, т.к. шифрование HTTPS требует дополнительных затрат.

+ Порты по умолчанию: в случае HTTP это TCP-порт `80`, для HTTPS - TCP-порт `443`.

[к оглавлению](#Основы-web)

## Чем отличаются методы HTTP/1.1 и HTTP/2?

Протокол HTTP/2  является бинарным. По сравнению с предыдущим стандартом изменены способы разбиения данных на фрагменты и транспортирования их между сервером и клиентом. В HTTP/2 сервер имеет право послать то содержимое, которое ещё не было запрошено клиентом. Это позволит серверу сразу выслать дополнительные файлы, которые потребуются браузеру для отображения страниц, без необходимости анализа браузером основной страницы и запрашивания необходимых дополнений. Также часть улучшений получена (в первом черновике HTTP/2, который представлял собой копию спецификации SPDY) за счёт мультиплексирования запросов и ответов для преодоления проблемы «head-of-line blocking» протоколов HTTP 1; сжатия передаваемых заголовков и введения явной приоритизации запросов.

[к оглавлению](#Основы-web)

## Какие серии кодов состояния есть в HTTP?

__Код состояния HTTP (англ. HTTP status code)__ — часть первой строки ответа сервера при запросах по протоколу HTTP. Он представляет собой целое число из трёх десятичных цифр. Первая цифра указывает на класс состояния. За кодом ответа обычно следует отделённая пробелом поясняющая фраза на английском языке, которая разъясняет человеку причину именно такого ответа.

+ __1xx__ (информационные)
    + _100 - Continue_
    + _101 - Switching Protocols_;
    + _102 - Processing_.
+ __2xx__
    + _200 OK_
    + _201 Created_
    + ...
+ __3xx__
    + _300 Multiple Choices_
    + _301 Moved Permanently_
    + _302 Moved Temporarily_
    + _302 Found_
    + ...
+ __4xx__
    + _400 Bad Request_
    + _401 Unauthorized_
    + _402 Payment Required_
    + _403 Forbidden_
    + _404 Not Found_
    + _405 Method Not Allowed_
    + _406 Not Acceptable_
    + _407 Proxy Authentication Required_
    + _408 Request Timeout_
    + ..
+ __5xx__
    + _500 Internal Server Error_
    + _501 Not Implemented_
    + _502 Bad Gateway_
    + _503 Service Unavailable_
    + _504 Gateway Timeout_
    + ...

[к оглавлению](#Основы-web)

## Чем отличаются методы _GET_ и _POST_?

__GET__ передает данные серверу используя URL, тогда как __POST__ передает данные, используя тело HTTP запроса. Длина URL ограничена 1024 символами, это и будет верхним ограничением для данных, которые можно отослать через GET. POST может отправлять гораздо большие объемы данных. Лимит устанавливается web-server и составляет обычно около 2 Mb.

Передача данных методом POST более безопасна, чем методом GET, так как секретные данные (например пароль) не отображаются напрямую в web-клиенте пользователя, в отличие от URL, который виден почти всегда. Иногда это преимущество превращается в недостаток - вы не сможете послать данные за кого-то другого.

[к оглавлению](#Основы-web)

## Чем отличаются методы _POST_, _PUT_ и _PATCH_?

Все эти методы использует тело HTTP запроса для передачи данных.

+ __POST__ —  используется для создания ресурса.
+ __PUT__ — используется для замены ресурса целиком.
+ __PATCH__ — используется для редактирования ресурса.

[к оглавлению](#Основы-web)

## Что такое _MIME тип_?

__MIME, Multipurpose Internet Mail Extension (Многоцелевые расширения Интернет-почты)__ — спецификация для передачи по сети файлов различного типа: изображений, музыки, текстов, видео, архивов и др. В HTML указание MIME-типа используется при  передаче данных форм и вставки на страницу различных объектов.

[к оглавлению](#Основы-web)

## Что такое _Web service_?

...

[к оглавлению](#Основы-web)

## Что такое _Web server_?

__Web server (Веб-сервер)__ — сервер, принимающий HTTP-запросы от клиентов и выдающий им HTTP-ответы. Так называют как программное обеспечение, выполняющее функции web-сервера, так и непосредственно компьютер, на котором это программное обеспечение работает.

Web-серверы могут иметь различные дополнительные функции, например:

+ автоматизация работы web-страниц;
+ ведение журнала обращений пользователей к ресурсам;
+ аутентификация и авторизация пользователей;
+ поддержка динамически генерируемых страниц;
+ поддержка HTTPS для защищённых соединений с клиентами.

Наиболее известные web-серверы:

+ Apache
+ Microsoft IIS
+ nginx

[к оглавлению](#Основы-web)

## Что такое _Web application_?

__Web application (Веб-приложение)__ - клиент-серверное приложение, в котором клиентом выступает браузер, а сервером — web-сервер. Логика web application распределена между сервером и клиентом, хранение данных осуществляется, преимущественно, на сервере, а обмен информацией происходит по сети. Одним из преимуществ такого подхода является тот факт, что клиенты не зависят от конкретной операционной системы пользователя, поэтому web application является кроссплатформенным сервисом.

[к оглавлению](#Основы-web)

## Что такое _Application server_?

__Application Server (Сервер приложений)__ — программа, представляющая собой сервер, который занимается системной поддержкой приложений и обеспечивает их жизненный цикл в соответствии с правилами, определёнными в спецификациях. Может работать как полноценный самостоятельный web-сервер или быть поставщиком страниц для другого web-сервера. Обеспечивает обмен данными между приложениями и клиентами, берёт на себя выполнение таких функций, как создание программной среды для функционирующего приложения, идентификацию и авторизацию клиентов, организацию сессии для каждого из них.

Наиболее известные серверы приложений Java:

+ Apache Tomcat
+ Jetty
+ JBoss
+ GlassFish
+ IBM WebSphere
+ Oracle Weblogic

[к оглавлению](#Основы-web)

## Чем отличаются _Web server_ и _Application server_?

Понятие web server относится скорее к способу передачи данных (конкретно, по протоколу HTTP), в то время как понятие Application server относится к способу выполнения этих самых приложений (конкретно, удаленная обработка запросов клиентов при помощи каких-то программ, размещенных на сервере). Эти понятия нельзя ставить в один ряд. Они обозначают разные признаки программы. Какие-то программы удовлетворяют только одному признаку, какие-то - нескольким сразу.

Apache Tomcat умеет выполнять приложения? Да, значит он является application server. Apache Tomcat умеет отдавать данные по HTTP? - Да. Следовательно он является web server.

Возьмите какую-нибудь базу данных, в которой на хранимых процедурах описана сложная логика и можно в ответ на SQL-запросы отправлять даже sms. Такую базу данных можно назвать application server, но web server - уже нет, потому что все это не работает с клиентом по HTTP протоколу.

Возьмите чистый Apache, в котором не включены никакие модули для поддержки языков программирования. Он умеет отдавать только статичные файлы и картинки по протоколу HTTP. Это web server, но не application server. Включите модуль для поддержки PHP и разместите там программу на PHP, которая делает запросы к базе данных и динамически формирует страницы. Теперь Apache стал и application server.

[к оглавлению](#Основы-web)

## Что такое _WebSocket_?

__WebSocket__ — протокол полнодуплексной связи поверх TCP-соединения, предназначенный для обмена сообщениями между браузером и web-сервером в режиме реального времени.

Протокол _WebSocket_ определяет две URI схемы

+ `ws:` - нешифрованное соединение
+ `wss:` - шифрованное соединение

[к оглавлению](#Основы-web)

## Что такое _cookies_?

__Cookies («куки»)__ — небольшой фрагмент данных, отправленный web-сервером и хранимый на устройстве пользователя. Всякий раз при попытке открыть страницу сайта, web-клиент пересылает соответствующие этому сайту cookies web-серверу в составе HTTP-запроса. Применяется для сохранения данных на стороне пользователя и на практике обычно используется для:

+ аутентификации пользователя;
+ хранения персональных предпочтений и настроек пользователя;
+ отслеживания состояния сеанса доступа пользователя;
+ ведения разнообразной статистики.

[к оглавлению](#Основы-web)

## Что такое _«сессия»_?

__Сессия__ – промежуток времени между первым и последним запросами, которые пользователь отправляет со своего устройства на сервер сайта. Завершается сессия в случае, если со стороны пользователя не поступало запросов в течение определенного промежутка времени или же при обрыве связи.

[к оглавлению](#Основы-web)

# Источники

+ [Википедия](https://ru.wikipedia.org/)

[Вопросы для собеседования](README.md)
