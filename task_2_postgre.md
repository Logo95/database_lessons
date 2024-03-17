### Отчёт о проделанной работе в PostgreSQL

#### Создание таблиц
```sql
-- Создание таблицы users
CREATE TABLE users (
    userId SERIAL PRIMARY KEY,
    userName VARCHAR(100),
    userLastname VARCHAR(100)
);

-- Создание таблицы chats
CREATE TABLE chats (
    chatId SERIAL PRIMARY KEY,
    chatName VARCHAR(100)
);

-- Создание таблицы messages
CREATE TABLE messages (
    messageId SERIAL PRIMARY KEY,
    userId INT,
    chatId INT,
    messageText TEXT,
    messageDate TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (userId) REFERENCES users(userId),
    FOREIGN KEY (chatId) REFERENCES chats(chatId)
);
```
#### заполнение таблиц
```sql
-- Заполнение таблицы users данными
INSERT INTO users (userName, userLastname) VALUES 
('John', 'Doe'),
('Alice', 'Smith'),
('Bob', 'Johnson');

-- Заполнение таблицы chats данными
INSERT INTO chats (chatName) VALUES 
('General'),
('Sales'),
('Support');

-- Заполнение таблицы messages данными
INSERT INTO messages (userId, chatId, messageText) VALUES 
(1, 1, 'Hello everyone!'),
(2, 1, 'Hi John!'),
(3, 1, 'Hey there!'),
(1, 2, 'Are there any updates on the sales report?'),
(3, 2, 'Not yet, John. We are still waiting for the data.'),
(1, 3, 'I need help with my account.'),
(2, 3, 'Sure, Alice. What seems to be the problem?');
```
#### Вывод таблиц
```sql
-- Вывод данных из всех трех таблиц
SELECT u.userId, u.userName, u.userLastname, c.chatId, c.chatName, m.messageId AS lastMessageId, m.messageText AS lastMessageText
FROM users u
JOIN messages m ON u.userId = m.userId
JOIN chats c ON m.chatId = c.chatId
ORDER BY m.messageDate DESC;
