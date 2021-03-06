# Присоединиться к чат-комнате
> POST /v1/rooms/{roomId}/join

## Запрос

Параметр | Обязательный | Описание
-|-|-
token | Да | Уникальный идентификатор сессии

## Ответ

### 200 OK
> Пользователь успешно присоединился к чат-комнате

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
> * Нет приглашения в закрытую чат-комнату

Поле | Тип | Описание
-|-|-
error | STRING | Сообщение об ошибке

```json
{
    'error': STRING
}
```

### 404 Not Found
> Чат-комната с указанным `{roomId}` не найдена

Поле | Тип | Описание
-|-|-
error | STRING | Сообщение об ошибке

```json
{
    'error': STRING
}
```
