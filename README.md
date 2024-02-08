## my-app (nazwa aplikacji) - developing with Docker

Projekt zakłada utworzenie trzech kontenerów Dockerowych, które będą zawierały FastAPI, PostgreSQL, SQLAlchemy oraz mechanizm uwierzytelniania JWT.
Aplikacja będzie miała pięć głównych funkcjonalności, w tym operacje CRUD na użytkownikach oraz uwierzytelnianie i autoryzację użytkowników za pomocą JWT.

Wszystkie komponenty w oparciu o Docker.

Kontenery:

1. Kontener FastAPI:
   zawiera serwer FastAPI obsługujący wszystkie funkcjonalności backendowe, w tym CRUD użytkowników, uwierzytelnianie JWT, rejestrację i logowanie.
2. Kontener PostgreSQL:
   zawiera bazę danych PostgreSQL, która przechowuje dane użytkowników.
3. Kontener JWT:
   zawiera serwer obsługujący uwierzytelnianie JWT.

Funkcjonalności:

1. CRUD Użytkowników (FastAPI):
   Umożliwia dodawanie, odczytywanie, aktualizowanie i usuwanie użytkowników w bazie danych PostgreSQL.
2. Uwierzytelnianie JWT (FastAPI):
   Zapewnia mechanizm uwierzytelniania JWT dla użytkowników, aby mogli się zalogować i uzyskać dostęp do chronionych zasobów.
3. Rejestracja (FastAPI):
   Umożliwia użytkownikom rejestrację nowych kont w systemie.
4. Logowanie (FastAPI):
   Zapewnia użytkownikom możliwość logowania się do systemu za pomocą nazwy użytkownika i hasła.
5. Przechowywanie danych (PostgreSQL):
   Kontener PostgreSQL przechowuje dane użytkowników, takie jak nazwa użytkownika, hasło i inne informacje profilowe.

### Uruchamianie z Dockerem

#### To start the application

Step 0 (alternatywa): sklonuj repozytorium

    ```bash
       git clone <adres-repozytorium>

Step 1: Create docker network

    docker network create postgres-network

Step 2: start BD

Step 3: start ORM

Step 4: open BD from browser

    http://localhost:8000

Step 5: create `user-account` _db_ and `users` _collection_ in ORM

Step 6: Start your application locally - go to `app` directory of project

       Przejdź do katalogu projektu:

       cd my-app

       Zbuduj obrazy kontenerów:

       docker build -t my-app_fastapi -f Dockerfile_fastapi .
       docker build -t my-app_postgresql -f Dockerfile_postgresql .
       docker build -t my-app_jwt -f Dockerfile_jwt .

       Uruchom kontenery:

       docker run -d --name fastapi -p 80:80 my-app_fastapi
       docker run -d --name postgresql nmy-app_postgresql
       docker run -d --name jwt -p 8000:8000 --link postgresql --link fastapi my-app_jwt

Step 7: Access you application UI from browser

    http://localhost:80

### Uruchamianie z Docker Composee

#### To start the application

Step 1: start BD , ORM

    docker-compose -f docker-compose.yaml up

_You can access ORMs under localhost:8000 from your browser_

Step 2: in UI - create a new database "my-db"

Step 3: in UI - create a new collection "users" in the database "my-db"

Step 4: start server

    npm install
    node server.js

Step 5: access application from browser

    http://localhost:

#### To build a docker image from the application

    docker build -t my-app:1.0 .

The dot "." at the end of the command denotes location of the Dockerfile.
