# Информация о чат-комнатах, в которых состоит пользователь
> GET /v1/users/{userId}/rooms

## Запрос

Параметр | Обязательный | Описание
-|-|-
token | Да | Уникальный идентификатор сессии
count | Нет | Количество записей (не более 50)
page | Нет | Номер страницы

## Ответ

### 200 OK
> Список чат-комнатах, в которых состоит пользователь

Поле | Тип | Описание
-|-|-
id | NUMBER | Уникальный ID чат-комнаты
title | STRING | Название чат-комнаты
private | BOOL | Признак частной (закрытой) чат-комнаты
adminID | NUMBER | ID пользователя (администратора) частной (закрытой) чат-комнаты

```json
[
    {
        id:      NUMBER,
        title:   STRING,
        private: BOOL,
        adminID: NUMBER
    }
]
```

> NOTE: Смотри описание модели `Chatroom`

> NOTE: Список не должен содержать закрытых чат-комнат за исключением следующих случаев:
> * Запрос инициирован самим пользователем
> * Запрос инициирован администратором закрытой чат-комнаты (в этом случае будут доступны только те чат-комнаты, администратором которых является запрашивающий)


### 401 Unauthorized
> Не указан токен

Поле | Тип | Описание
-|-|-
error | STRING | Сообщение об ошибке

```json
{
    'error': STRING
}
```

### 403 Forbidden
> Доступ запрещён
> * Указан недействительный токен

Поле | Тип | Описание
-|-|-
error | STRING | Сообщение об ошибке

```json
{
    'error': STRING
}
```

### 404 Not Found
> Не найдено записей, удовлетворяющих запросу (некоректный `{userId}`)

Поле | Тип | Описание
-|-|-
error | STRING | Сообщение об ошибке

```json
{
    'error': STRING
}