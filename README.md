# y&&y ДЗ «Реакт. Построение приложения»

Для связи tg: @nmonteg

## Сборка и запуск проекта

1. Установка зависимостей:

   ```bash
   npm install
   ```

2. Сборка и запуск проекта:

   ```bash
   npm run dev
   ```

3. Для полноценной работы необходим сервис "Фильмопоиска"

   [Скачать](https://disk.yandex.ru/d/89vxMorGgTVKCg) и выполнить следующие команды:

   ```bash
   npm install

   npm run start:main
   ```

   В отдельном терминале выполнить следующую команду:

   ```bash
   npm run start:actors
   ```

   #### Дополнительные команды

- Проверка файлов проекта в соответствии с eslint, форматирование с помощью prettier:

  ```bash
  npm run lint
  ```

- Проверка типов TypeScript:
  ```bash
  npm run format
  ```

## Описание технических параметров

- [Макет проекта в Figma](https://www.figma.com/design/ucG4WHfOZOEa5GtnXzGs7M/%D0%9C%D0%B0%D0%BA%D0%B5%D1%82%D1%8B-%D0%91%D0%B8%D0%BB%D0%B5%D1%82%D0%BE%D0%BF%D0%BE%D0%B8%D1%81%D0%BA?node-id=0-1&t=7nytVuHIaA51LLZj-0).
- Реализован стейт-менеджер Redux-toolkit;
- API-запросы выполняются с помощью rtk query;
- Проект написан с помощью typescript;
- Добавлены линтер и форметтер для кода: ESLint, Prettier;
- Стили реализованы с помощью CSS Modules
- Для роутинга используется react-router-dom

## Основные требования к проекту и их реализация

Функциональные требования:

- Шапка:

  - Позиционируется липко (стики) - ✅

- Авторизация:

  - Для реализации модального окна используется портал - ✅
  - После успешной авторизации кнопка «Войти» меняется на заглушку иконки пользователя и кнопку «Выйти» - ✅
  - Сохраняем авторизационный токен из ответа ручки бэка /login (например, в localStorage) - ✅
  - С токеном стоит работать через thunk - ❌
  - По клику на кнопку «Выйти» удаляем токен и снимаем авторизацию - ✅
  - При инициализации приложения проверяем авторизационный токен - ✅

- Реализована страница списка фильмов

  Поиск:

  - Поиск происходит во время ввода пользователем символов. Дёргаем ручку /search - ✅
    Фильтры:
    Реализованы фильтры с dropdown - ✅
    Фильтры сохраняются в query-params - ✅
    Реализован список фильмов с пагинацией - ✅

  Страница фильма:

  - Реализована работа с получением данных - ✅
  - Дёргаем ручку /movie:id, соответствующие данные отрисованы - ✅

  Возможность поставить оценку:

  - Оценку для фильма достаём из ручки /movie/:id - ✅
  - Если пользователь авторизован, даём возможность поставить оценку — запрос мутации (после этой домашки я скоро сам мутировать начну) - ✅
  - После выставления оценки обновляем кеш запроса /movie/:id - ❌
  - Проставленную оценку храним в local Storage - ✅

  Общий функционал:

Реализовать единообразную обработку ошибок для запросов;

- Реализован лоадер - ✅
- Используем debounce для поиска фильма и выставления оценки - ✅

Стор:
(тут все субъективно, но как мне кажется, сделал не громоздко)

- Используется rtk и rtk-query - ✅
- Данные корректно разбиты на модули (пример — авторизация, searchParams из фильтров) - ✅
- Селекторы написаны оптимально (нет переизбытка дублирования) - ✅

Миграция на Next - ❌

- Реализована миграция с использованием SSR - ❌
- Для картинок используется Image некста. Скрины фильма, которые вне вьюпорта грузятся лениво - ❌
- Фильтры реализованы с помощью сегментов вместо query-параметров - ❌
