# project
## 27.06 11:00. Штаб-квартира ИИ

Приглушенный холодный свет. Электронный голос. Мигание красных светодиодов.

Времени нет. 

Не задавай лишний вопросов.

Просто выполняй инструкции.

## 27.06 11:01. Платформа
У тебя есть ссылка на git-репозиторий. Да, вот эта. Склонируй ее.

Создай ветку develop. Прямо из master.

В папке src в корне репозитория создай проект.

Любой язык программирования, из тех, что у тебя под рукой: Python, Java, C#, Go, JS. Любые библиотеки и фреймворки. Никаких ограничений. 

Это будет web-сервис c HTTP-API. Умный web-сервис. Но пока не думай об этом.
 
## 27.06 11:02. Папка src, сервис и HTTP API
Почему ты еще здесь, а проект не создан? Поторопись!

У тебя должен получиться простой web-сервис, который поддерживает один единственный эндпоинт API на базе протокола HTTP 1.1:

```
openapi: 3.0.0
info:
  title: Task API
  description: API для решения задач
  version: 1.0.0
servers:
  - url: localhost:8080
paths:
  /tasks:
    post:
      summary: Решить задачу
      description: Принимает данные о задаче и решает ее
      requestBody:
        description: Данные о задаче
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                task_description:
                  type: string
                  description: Описание задачи
                task_schema:
                  type: string
                  description: Схема задачи
                actions:
                  type: array
                  items:
                    type: string
                  description: Список возможных действий
                max_count:
                  type: integer
                  description: Максимальное количество действий
      responses:
        '200':
          description: Задача решена
          content:
            application/json:
              schema:
                type: object
                properties:
                  commandList:
                    type: array
                    items:
                      type: string
        '400':
          description: Задача не решена, так как формат данных неверный
          content:
            application/json:
              schema:
                type: object
                properties:
                  commandList:
                    type: array
                    items:
                      type: string
```
Да, да. Знаю, какие у тебя мысли. Нейминги не консистентны. Эхо вечной битвы... Шучу. Просто, как обычно, фронтенд с бекендом не могут договориться. 

## 27.06 11:03. Docker World
В папке src расположи Dockerfile.

Dockerfile твоего сервиса, разумеется. 

Он должен быть так написан, чтобы с его помощью полностью собирался твой сервис, а при запуске контейнера web-сервис запускался бы автоматически.

## 27.06 11:04. Достаточно
На этом достаточно. 

## 27.06 11:05. Шутка. Шутка и мок
Шутка, конечно.

Сервис нужно замокать.

Сервис должен обрабатывать 2 моковых запроса. 

Запрос первый.

Вход:
```
{
  "task_description": "TEST MOCK TASK",  
  "task_schema": "",
  "actions": [],
  "max_count": 0,
}
```
Ожидаемый выход:
```
200
{
  "commandList": ["TEST MOCK SUCCESS"],
}
```
Запрос второй.

Вход:
```
{
  "task_description": "TEST MOCK TASK",
  "actions": "",
}
```
Ожидаемый выход:

```
400
{
  "commandList": ["ERROR"],
}
```

## 27.06 11:06. Зона особого контроля
Что окажется под особым вниманием?

Это просто:

1.	Сборка Docker.
2.	Запуск Docker.
3.	Запуск web-сервиса на порту 8080.
4.	Обработка необходимых эндпоинтов.
5.	Обработка моковых запросов.
6.	Кажется, больше ничего.
7.	Да, точно, ничего. Пока ничего.


Так у тебя всё есть) Бери и делай. Как я тут вообще помогу?)))


Да уж ты прав.




#include <stdio.h>

#include "fcgi_stdio.h"

int main(void){
    while (FCGI_Accept() >= 0) {
        printf("Content-type: text/html\r\nStatus: 200 OK\r\n\r\nHello World!");
    }
    return 0;
}





https://infostart.ru/1c/articles/1426964/
