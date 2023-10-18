# Test-API-Issue

---
## Шаг 1 - создать token:
<p>1.Создайте токен API в своем профиле на GitHub</p>
    
<code>Settings  -> Developer settings -> Personal access token -> Token classics</code>
    
<p>2.Кнопка включения <code>Generate new token</code> </p>
<p>3.Возьмите имя ключа, назначьте разрешения</p>
<p>4.Нажмите кнопку <code>Сгенерировать токен</code></p>



---
## Шаг 2 - Postman
<p>1.Создайте новую коллекцию Postman</p>
     
 Выберите <code>Authorization -> Type -> Bearer Token</code>

<p>3.Введите свой токен с Github и сохраните изменения</p>


---
## Шаг 3 - Методы
[General GitHub REST API docs](https://docs.github.com/en/rest/issues/issues?apiVersion=2022-11-28#about-issues)


#### GET для получения информации о списке issues

- PATH: - <code>https://api.github.com/repos/{owner}/{repo}/issues</code>
- Authorization: - <code>inherit auth from parent</code>

#### POST для создания новой issue
- PATH: - <code>https://api.github.com/repos/{owner}/{repo}/issues</code>
- Authorization: - <code>inherit auth from parent</code>
- Body:

```
{
    "title": "issue_1",
    "body": "Something went wrong",
    "assignee": "KirillFv",
    "labels": [
        "bug"
    ]
}
```

- ##### Test,Script для получения номера issue
```
var key = "num"
var value = pm.response.json().number
pm.collectionVariables.set(key, value);
```


#### PATCH - для обновления issue
- PATH: - <code>https://api.github.com/repos/{owner}/{repo}/issues/{issue_number}</code>
- Use a variables from previous step - script
- Authorization: - <code>inherit auth from parent</code>
- Body (example):

```
{
    "title": "issue_2"
}
```

#### PUT - для блокировки issue
- PATH: - <code>https://api.github.com/repos/{owner}/{repo}/issues/{issue_number}/lock</code>
- Use a variables from previous step - script
- Authorization: - <code>inherit auth from parent</code>
- Body (example):

```
 {
         "locked": "true"     
 }

```

#### GET проверка блокировки issue
PATH: - <code>https://api.github.com/repos/{owner}/{repo}/issues/{issue_number}</code>
Use a variables from previous step - script
Authorization: - <code>inherit auth from parent</code>

#### DELETE (close) issue
PATH - <code>https://api.github.com/repos/{owner}/{repo}/issues/{issue_number}</code>
Authorization: - <code>inherit auth from parent</code>
body:

```
{
    "state": "close"
}
```


---
