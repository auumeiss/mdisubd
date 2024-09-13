# mdisubd
МОДЕЛИ ДАННЫХ и СИСТЕМЫ УПРАВЛЕНИЯ БАЗАМИ ДАННЫХ

Тема: Магазин мебели от заводов

Севрюков Степан Иванович 253504 

Функциональные требования к проекту:
  Авторизация и аутентификация пользователей:

    Поддержка различных ролей (покупатель, продавец, администратор).
    Разграничение прав доступа в зависимости от роли пользователя.
  Управление пользователями (CRUD):

    Администратор имеет возможность управлять пользователями (создавать, редактировать, удалять, просматривать).
  Система ролей:

    Разделение пользователей на группы с разными правами доступа (администратор, продавец, покупатель).
  Журналирование действий пользователя:

    Запись действий пользователей для отслеживания активности и аудита.
  Управление мебелью:

    Продавцы могут добавлять, редактировать и удалять мебель из системы, смотреть статистику по отдельным предметам мебели.
  Создание и управление заказами:

    Покупатели могут создавать заказы, просматривать историю заказов.
  Категоризация мебели:

    Поддержка различных категорий мебели с возможностью привязки мебели к категории.
  Управление отзывами:

    Покупатели могут оставлять отзывы на купленную мебель.


Перечень сущностей базы данных:
Points (Пункты продаж):

    ID (PK, INT): Уникальный идентификатор пункта продаж.
    NameOfPoint (VARCHAR): Название пункта продаж.
Seller (Продавец):

    ID (PK, INT): Уникальный идентификатор продавца.
    CompanyName (VARCHAR): Название компании продавца.
    Login (VARCHAR): Логин для авторизации.
    Password (VARCHAR): Пароль для авторизации.
    Email (VARCHAR): Электронная почта продавца.
    Phone (VARCHAR): Телефон продавца.
    Points (FK, INT): Внешний ключ, ссылающийся на Points. - ManyToMany
Furniture (Мебель):

    ID (PK, INT): Уникальный идентификатор мебели.
    Name (VARCHAR): Название мебели.
    Description (TEXT): Описание мебели.
    Price (DECIMAL): Цена мебели.
    IsAvailable (BOOL): Доступность товара.
    Seller (FK, INT): Внешний ключ, ссылающийся на Seller - ManyToOne
    FurnCategory (FK, INT): Внешний ключ, ссылающийся на FurnitureCategory - ManyToOne
FurnitureCategory (Категория мебели):

    ID (PK, INT): Уникальный идентификатор категории.
    Category (VARCHAR): Название категории.
Order (Заказ):

    ID (PK, INT): Уникальный идентификатор заказа.
    Date (DATETIME): Дата создания заказа.
    isOrdered (BOOL): Статус заказа.
    User (FK, INT): Внешний ключ, ссылающийся на Customer - OneToOne
    Price (DECIMAL): Общая стоимость заказа.
OrderedFurn (Заказанная мебель):

    ID (PK, INT): Уникальный идентификатор записи.
    Furniture (FK, INT): Внешний ключ, ссылающийся на Furniture - ManyToMany
    Count (INT): Количество заказанной мебели.
Customer (Покупатель):
    
    ID (PK, INT): Уникальный идентификатор покупателя.
    Name (VARCHAR): Имя покупателя.
    Login (VARCHAR): Логин покупателя.
    Password (VARCHAR): Пароль покупателя.
    Email (VARCHAR): Электронная почта покупателя.
Reviews (Отзывы):
    
    ID (PK, INT): Уникальный идентификатор отзыва.
    Customer (FK, INT): Внешний ключ, ссылающийся на Customer - OneToOne
    Text (TEXT): Текст отзыва.
    Date (DATETIME): Дата оставления отзыва.
    Grade (INT): Оценка (1-5).
Admin (Администратор):

    ID (PK, INT): Уникальный идентификатор администратора.
    Login (VARCHAR): Логин администратора.
    Password (VARCHAR): Пароль администратора.
    Email (VARCHAR): Электронная почта администратора.
ActionLog (Журнал действий):

    ID (PK, INT): Уникальный идентификатор записи журнала.
    Customer (FK, INT): Внешний ключ, ссылающийся на Customer - ManyToOne
    Action (VARCHAR): Действие, совершенное пользователем.
    Date (DATETIME): Дата и время действия.
Points-Seller (Промежуточная таблица для связи пунктов продаж и продавцов):

    ID (PK, INT): Уникальный идентификатор записи.
    Points (FK, INT): Внешний ключ, ссылающийся на Points.
    Seller (FK, INT): Внешний ключ, ссылающийся на Seller.
Furniture-OrderedFurn (Промежуточная таблица для связи мебели и заказанной мебели):
    
    ID (PK, INT): Уникальный идентификатор записи.
    Furniture (FK, INT): Внешний ключ, ссылающийся на Furniture.
    OrderedFurn (FK, INT): Внешний ключ, ссылающийся на OrderedFurn.


![БДШКИ drawio](https://github.com/user-attachments/assets/de8692e4-18be-4881-ac48-849726d0b8c2)


