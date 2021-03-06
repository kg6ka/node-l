# Lesson 6. Middleware. Templates. Mail.

----
## Lecture

**Video Link** [Webinar Video 6](https://youtu.be/OR5Vf58vSks)

***Video timing***

1.	[Middleware]( https://youtu.be/OR5Vf58vSks#t=23m26s)
2.	[app.get]( https://youtu.be/OR5Vf58vSks#t=24m39s)
3.	[Function requestTime]( https://youtu.be/OR5Vf58vSks#t=34m02s)
4.	[Порядок в middleware]( https://youtu.be/OR5Vf58vSks#t=43m20s)
5.	[Модуль connect и метод static]( https://youtu.be/OR5Vf58vSks#t=55m20s)
6.	[Модули express]( https://youtu.be/OR5Vf58vSks#t=62m35s)
7.	[Модуль body-parser]( https://youtu.be/OR5Vf58vSks#t=62m48s)
8.	[Модуль CORS]( https://youtu.be/OR5Vf58vSks#t=66m43s)
9.	[Шаблонизатор JADE]( https://youtu.be/OR5Vf58vSks#t=83m10s)
10. [Шаблонизатор Handlebars]( https://youtu.be/OR5Vf58vSks#t=84m05s)
11. [Шаблонизатор ejs]( https://youtu.be/OR5Vf58vSks#t=97m47s)
12. [Mail]( https://youtu.be/OR5Vf58vSks?t=6310)


----
## Homework

Неодбходимо создать приложение на express.js (или koa).

### 1. Home page html

Форма должна содердать такие поля:
* Имя `[type=text]`
* Фамилия `[type=text]`
* Телефон `[type=tel]`
* Email `[type=email]`
* Продукт `[type=select]`
    * Молоко
    * Хлеб
    * Картошка
    * Курица
    * Соль
* Заказать `[type=submit]`

При сабмите формы отправляем запрос `POST /order/`.

### 2. Шаблонизировать home page

При запросе `GET /` — должна отдаваться html страница  `home page` с формой.
Её необходимо отдавать через шаблонизатор (handlebars, ejs, jade — на ваш выбор).

### 3. Обработка заказа

Необходимо создать обработчик на `POST /order/`.

В случае если нет никаких ошибок — то отправляем ответ со статическим html `Ваш заказ успешно принят. ID заказа 9999`

Id заказа - это рандомное число `от 0 до 9999`.

html этой страницы необходмо шаблонизировать.

### 3. Manger mail

Добавляем в обработчик `POST /order/` отправку письма менеджеру.
 
При получении запроса необходимо отправлять письмо с заказом менеджеру магазина. Email получателя поставьте ваш личный.

Необходимо создать html шаблон письма (используя шаблонизатор) с текстом и предавать в него параметры заказа.
В письме должны быть следующие данные: 
 
 * Имя
 * Фамимлия
 * Телефон 
 * Email 
 * Продукт 
 * Дата и время заказа
 * id заказа 

Заголовок письма должнен быть: `Заказ 9999. Имя Фамилия` 

### 3. Client mail

На `POST /order/` необходимо также добавить отправку письма самому пользователю.
Шаблон с текстом письма должен быль в отдельном файле шаблонизатора.

В это письмо должно передаваться:

* Продукт 
* Дата и время заказа
* id заказа 

Заголовок письма должнен быть: `Ваш заказ 9999 в магазине Ларёк принят`

### 4. Валидации

На входящие запросы на `POST /order/` необходимо добавить проверку входящих данных.

1. Обязательные поля: все поля обязательыны для заполнения (должны быть не пустыми). `error_id=required_field`
2. Добавить к обработке формы валидацию email. `error=invalid_email`
3. Добавить к обработке формы валидацию телефона. `error=invalid_tel`

В случае ошибки редиректим пользователя на url `/?error=error_id`
 
### 5. Обработка ошибок в шаблоне 

При запросе `GET /` необходимо сделать проверку есть ли GET параметр `?error=error_id`

Если есть то в шалоне нужно вывести блок с обшибкой. Текст ошибки должен соответсвовать типу ошибки. 
Например: `Вы не заполнили все обязательные поля`.

### Примечания

* Выносите в отдельный конфиг все что может меняться в последствии: 
email менеджера, authn credentials для почтового ящика с кторого отправляются письма.
* Подключите какой-то готовый css framework (bootstrap).
* Добавьте static middleware для выдачи статики.
* Вынестие в отдельный конфиг id ошибок и тексты.
* Вынестие в отдельный модуль валидаторы.
    
----
## Links

1. [Writing middleware (ru)](http://expressjs.com/ru/guide/writing-middleware.html)
2. [Using middleware (ru)](http://expressjs.com/ru/guide/using-middleware.html)
3. [Middleware list](http://expressjs.com/ru/resources/middleware.html)
4. [CORS](https://www.npmjs.com/package/cors)
5. [Routing](http://expressjs.com/ru/guide/routing.html)
6. [ejs](http://www.embeddedjs.com)
7. [Handlebars](http://handlebarsjs.com)
8. [npm express-handlebars](https://www.npmjs.com/package/express-handlebars)
9. [Nodemailer](https://nodemailer.com)
