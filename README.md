# TMDB
Набор скриптов для работы с [TheMovieDB](https://www.themoviedb.org/).


## Setup
1. Get your personal API key [https://www.themoviedb.org/documentation/api](https://www.themoviedb.org/documentation/api)

2. Clone project
```bash
git clone https://github.com/gennadis/tmdb_api.git
cd tmdb_api
```

3. Create virtual environment
```bash
python3 -m venv venv
source venv/bin/activate
```

4. Install requirements
```bash
pip install -r requirements.txt
```

5. Make test API query. You should get Saw II movie budget.
```bash
python hello_api_TMDB.py
```

6. Build your own local database. Fetch information of a thousand films.
```bash
python make_own_db.py
```




## find_similar.py
Скрипт выдает рекомендации с фильмами, похожими на тот, что ему передает пользователь.  
Вначале скрипт спрашивает путь до файла с локальной БД, затем принимает название фильма от пользователя, далее выводит отсортированный список подходящих по параметрам фильмов (по умолчанию - 8 рекомендаций).

---

## hello_api_TMDB
Тестовый скрипт.
При запуске скрипт запрашивает апи-ключ пользователя. Если ключ проходит авторизацию, то выводит значение параметра `budget` фильма с [id == 215](https://www.themoviedb.org/movie/215-saw-ii).

---

## make_own_db
Данный скрипт скачивает и пишет в `json` первую тысячу наборов информации о фильмах (id 1 -> id 1000).
При запуске запрашивает и валидирует апи-ключ, далее начинает скачивание, после завершения которого пишет собраннуж информацию в файл.

---

## own_db_helpers
Считывает данные из `json` файла по указанному пути.

---

## search_in_db
Проводит базовый текстовый поиск по локальной базе фильмов и возвращает отсортированный список названий фильмов.
При запуске спрашивает путь до локальный базы фильмов, далее спрашивает клчевое слово для поиска, после чего проводит поиск фильмов с названием, содержащим ключевое слово. Выводит результат в виде отсортированного списка названий.

---

## tmdb_helpers
Набор функций, используемых в остальных модулях программы.
`make_tmdb_api_request`: создает набор параметров, с которыми вызывает функицю ниже 
`load_json_data_from_url`: совершает запрос и возвращает json-объект ответа TMDB 
`get_user_api_key`: запрашивает апи-ключ пользователя и проводит его валидацию путем простого запроса