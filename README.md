# mdisubd
МОДЕЛИ ДАННЫХ и СИСТЕМЫ УПРАВЛЕНИЯ БАЗАМИ ДАННЫХ

Тема: Магазин мебели от заводов

Севрюков Степан Иванович 253504 

Функциональные требования к проекту:
  Авторизация и аутентификация пользователей:

    Поддержка различных ролей (покупатель, продавец, администратор).
    Разграничение прав доступа в зависимости от роли пользователя.
    
  Администратор:

    Управление пользователями (CRUD)
    создание отзыва
    просмотр статистики по продажам мебели
    
  Продавец:
  
    Управление мебелью (CRUD)
    создание категорий мебели
    просмотр статистики по предметам мебели и продажам
    
 Покупатель:

    Покупка мебели
    составление заказа
    
  Все пользователи:
  
    создание отзыва
    поиск по мебели
    фильтр по мебели
    

    

Логирование каждого пользователя


Перечень сущностей базы данных:
Role (роли):

    ID (PK, int) -  Уникальный идентификатор.
    Name(string) - Название роли. 
    Permission_id(int, not null, fk to permission) - Внешний ключ на разрешения для роли - ManyToMany.
Points (Пункты продаж):

    ID (PK, INT): Уникальный идентификатор пункта продаж.
    NameOfPoint (VARCHAR, 100): Название пункта продаж.

User (пользователь):
    
    ID (PK, INT): Уникальный идентификатор
    Login (VARCHAR,50): Логин для авторизации.
    Password (VARCHAR,50): Пароль для авторизации.
    Email (VARCHAR,50): Электронная почта.
    Role_ID(INT) - Ключ, ссылающийся на роль - OneToMany
    
Seller (Продавец):

    ID (PK, INT): Уникальный идентификатор продавца.
    CompanyName (VARCHAR,50): Название компании продавца.
    Phone (VARCHAR,50): Телефон продавца.
    Points (FK, INT): Внешний ключ, ссылающийся на Points. - ManyToMany
    User_Id(INT, not null) - Внешний ключ, ссылающийся на User - OneToOne
Furniture (Мебель):

    ID (PK, INT): Уникальный идентификатор мебели.
    Name (VARCHAR,50): Название мебели.
    Description (TEXT,250): Описание мебели.
    Price (DECIMAL): Цена мебели.
    IsAvailable (BOOL): Доступность товара.
    Seller (FK, INT): Внешний ключ, ссылающийся на Seller - ManyToOne
    FurnCategory (FK, INT): Внешний ключ, ссылающийся на FurnitureCategory - ManyToOne
FurnitureCategory (Категория мебели):

    ID (PK, INT): Уникальный идентификатор категории.
    Category (VARCHAR,50): Название категории.
Order (Заказ):

    ID (PK, INT): Уникальный идентификатор заказа.
    Date (DATETIME): Дата создания заказа.
    isOrdered (BOOL): Статус заказа.
    User_id (FK, INT): Внешний ключ, ссылающийся на Customer - ManyToOne
    Price (DECIMAL): Общая стоимость заказа.
    OrderedFurniture_id (int, not null, FK to "OrderedFurn") - Внешний ключ на OrderedFurn - OneToMany
OrderedFurn (Заказанная мебель):

    ID (PK, INT): Уникальный идентификатор записи.
    Furniture (FK, INT): Внешний ключ, ссылающийся на Furniture - ManyToMany
    Count (INT): Количество заказанной мебели.
Customer (Покупатель):
    
    ID (PK, INT): Уникальный идентификатор покупателя.
    Name(VARCHAR, 50) : Имя пользователя
    Surname(VARCHAR, 50) - Фамилия
    Phone (VARCHAR, 50) - Телефон
    User_Id(int, not null, FK to User) - Внешний ключ на пользователя, OneToOne
Reviews (Отзывы)
    
    ID (PK, INT): Уникальный идентификатор отзыва.
    User (FK, INT): Внешний ключ, ссылающийся на User - OneToOne
    Text (TEXT,250): Текст отзыва.
    Date (DATETIME): Дата оставления отзыва.
    Grade (INT): Оценка (1-5).
Admin (Администратор):

    ID (PK, INT): Уникальный идентификатор администратора.
    User_Id(int, not null, FK to User) - Внешний ключ на пользователя, OneToOne
ActionLog (Журнал действий):

    ID (PK, INT): Уникальный идентификатор записи журнала.
    User_id (FK, INT): Внешний ключ, ссылающийся на User - ManyToOne
    Action (VARCHAR,250): Действие, совершенное пользователем.
    Date (DATETIME): Дата и время действия.
Points-Seller (Промежуточная таблица для связи пунктов продаж и продавцов):

    ID (PK, INT): Уникальный идентификатор записи.
    Points (FK, INT): Внешний ключ, ссылающийся на Points.
    Seller (FK, INT): Внешний ключ, ссылающийся на Seller.
Furniture-OrderedFurn (Промежуточная таблица для связи мебели и заказанной мебели):
    
    ID (PK, INT): Уникальный идентификатор записи.
    Furniture (FK, INT): Внешний ключ, ссылающийся на Furniture.
    OrderedFurn (FK, INT): Внешний ключ, ссылающийся на OrderedFurn.



![БДШКИ drawio (2)](https://github.com/user-attachments/assets/df109473-7dc1-440b-b7a2-6a1b3710d2ac)



