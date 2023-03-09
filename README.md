# Api

## GET /api/data

### Middleware: auth

### Тело ответа

```json
{
  "hello": "world"
}
```

## POST api/auth/signup

### Тело запроса

```json
{
	"username": ...,
	"password": ...,
	"repeatPassword": ...
}
```

### Валидация

- `username` от 3 до 12 символов
- `password` от 6 до 30
- `repeatPassword` совпадает с `password`

### Тело ответа

```json
{
	"user": {
		"id": [uuid].,
		"name": ...,
	},
	"accessToken": ...,
	"refreshToken": ...,
}
```

#### Соokie

- `refreshToken` : ...
  - `httpOnly`: true
  - `maxAge`: 1000 * 60 * 60 * 30 (1 месяц)

## POST api/auth/login

### Тело запроса

```json
{
	"username": ...,
	"password": ...,
}
```

### Тело ответа

```json
{
	"user": {
		"id": [uuid].,
		"name": ...,
	},
	"accessToken": ...,
	"refreshToken": ...,
}
```

#### Соokie

- `refreshToken` : ...
  - `httpOnly`: true
  - `maxAge`: 1000 * 60 * 60 * 30 (1 месяц)

## GET api/auth/refresh

### Тело запроса

#### Cookie

- `refreshToken`

### Тело ответа

```json
{
	"user": {
		"id": [uuid].,
		"name": ...,
	},
	"accessToken": ...,
	"refreshToken": ...,
}
```

#### Соokie

- `refreshToken` : ...
  - `httpOnly`: true
  - `maxAge`: 1000 * 60 * 60 * 30 (1 месяц)

## GET api/auth/logout

### Тело запроса

#### Cookie

- `refreshToken`

### Тело ответа

#### Соokie

- `refreshToken` : удалить, а не отдавать
