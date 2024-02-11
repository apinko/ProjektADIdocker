
# Wybierz obraz bazowy
FROM python:3.8.10-slim

WORKDIR /app
###RUN mkdir -p /home/backend

COPY . /app
# Skopiuj pliki aplikacji do kontenera
###COPY ./backend  /home/backend

# Zainstaluj zależności
RUN pip install --upgrade pip && pip install fastapi uvicorn[standard]  SQLAlchemy
### -r requirements.txt

# Otwórz port, na którym będzie działać serwer
EXPOSE 8000




# # Wybierz obraz bazowy
# FROM tiangolo/uvicorn-gunicorn-fastapi:python3.9

# # Skopiuj pliki aplikacji do kontenera
# COPY ./app /app

# # Zainstaluj zależności
# RUN pip install --upgrade pip && pip install fastapi uvicorn[standard] python-dotenv psycopg2-binary PyJWT SQLAlchemy

# # Otwórz port, na którym będzie działać serwer
# EXPOSE 80