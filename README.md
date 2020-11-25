# Django-API-Development

Доработать созданный API в Django, используя Django REST Framework (DRF)

1. Добавить модель "Category". Установить отношение между моделями "Post" и "Category".
   Для простоты лучше исходить из того, что к посту может относиться только одна категория, но к одной категории может относиться множество постов.

Категория должна быть необязательным параметром поста. При удалении категории у всех связанных постов категория должна становиться равной null, то есть обнуляться.

2. Добавить категории в API, то есть создать обработчики и сериализаторы (полезно будет освежить память о вложенных связях в DRF).

Маршруты вашего приложения должны быть связаны с обработчиками списка категорий и единичной категорией:
https://YOUR_HOST/categories/ и https://YOUR_HOST/categories/<int:pk> соответственно.

При этом на запрос GET по адресу https://YOUR_HOST/categories/ сервер должен отвечать списком всех категорий и входящих в них постов.
По запросу POST на этот адрес должна создаваться новая категория, а информация о ней должна возвращаться в качестве ответа сервера с HTTP статусом 201 (created).

На запрос GET по адресу https://YOUR_HOST/categories/<int:pk> сервер должен отображать информацию только об одной категории, id которой был передан в запросе.

Админка: https://intense-harbor-08686.herokuapp.com/admin/login/?next=/admin/
Логин: 1
Пароль: 1

Список всех постов: https://intense-harbor-08686.herokuapp.com/
Информация про конкретный пост: https://intense-harbor-08686.herokuapp.com/{номер поста}

Список категорий с входящими в них постами:
https://intense-harbor-08686.herokuapp.com/categories/

Список постов в опеделённой категории:
https://intense-harbor-08686.herokuapp.com/categories/{номер категории}

Создание категории:
new_item = requests.post('https://intense-harbor-08686.herokuapp.com/categories/', data={'name': 'requests item'})
Ответ, включающий ID категории для последующего добавления постов:
new_item.json()
{'id': 4, 'name': 'requests item', 'posts': []}

Создание поста в новой категории:
new_post = requests.post('https://intense-harbor-08686.herokuapp.com/', data={'title': 'пост', 'author': '1', 'category': '4', 'status': 'P', 'content': 'содержимое 6'})
new_post.json()

Посмотреть созданную категорию и пост в ней:
https://intense-harbor-08686.herokuapp.com/categories/{номер категории}

Refine the generated API in Django using the Django REST Framework (DRF)

1. Add the "Category" model. Establish a relationship between the "Post" and "Category" models.
   For simplicity, it's best to assume that only one category can belong to a post, but many posts can belong to one category.

Category should be an optional post parameter. When deleting a category for all related posts, the category must become equal to null, that is, zeroed out.

2. Add categories to the API, that is, create handlers and serializers (it will be useful to refresh your memory about nested links in DRF).

Your app's routes should be associated with category list handlers and a single category:
https: // YOUR_HOST / categories / and https: // YOUR_HOST / categories / <int: pk> respectively.

At the same time, the server should respond to a GET request at https: // YOUR_HOST / categories / with a list of all categories and posts included in them.
Upon a POST request, a new category should be created to this address, and information about it should be returned as a server response with HTTP status 201 (created).

For a GET request to the address https: // YOUR_HOST / categories / <int: pk>, the server should display information about only one category, the id of which was passed in the request.

Admin panel: https://intense-harbor-08686.herokuapp.com/admin/login/?next=/admin/
Login: 1
Password: 1

List of all posts: https://intense-harbor-08686.herokuapp.com/
Information about a specific post: https://intense-harbor-08686.herokuapp.com/ {post number}

List of categories with posts included in them:
https://intense-harbor-08686.herokuapp.com/categories/

List of posts in a specific category:
https://intense-harbor-08686.herokuapp.com/categories/ {category number}

Category creation:
new_item = requests.post ('https://intense-harbor-08686.herokuapp.com/categories/', data = {'name': 'requests item'})
Answer including category ID for adding posts later:
new_item.json ()
{'id': 4, 'name': 'requests item', 'posts': []}

Create a post in a new category:
new_post = requests.post ('https://intense-harbor-08686.herokuapp.com/', data = {'title': 'post', 'author': '1', 'category': '4', 'status': 'P', 'content': 'content 6'})
new_post.json ()

View the created category and the post in it:
https://intense-harbor-08686.herokuapp.com/categories/ {category number}
