# Урок № 82: HTML. CSS. JavaScript
## 1. Сборка проекта
Выполните команду для сборки проекта и создания WAR-файла:

```bash
mvn clean package
```
После выполнения команды Maven создаст файл homework082.war в папке target.
## 2. Установка сервера приложений
Для запуска веб-приложения вам нужен сервер приложений. Наиболее распространённый — Apache Tomcat. Вот как установить и настроить его:

### 1) Скачивание Apache Tomcat:

- Перейдите на официальный сайт Apache Tomcat.
- Скачайте последнюю стабильную версию (например, Tomcat 9 или Tomcat 10).
### 2) Установка Apache Tomcat:

- Распакуйте архив в удобное место на вашем компьютере.
Например, путь может быть: C:\apache-tomcat-9.0.x.
### 3) Проверка работы Tomcat:

- Перейдите в папку bin внутри распакованного Tomcat.
### 4) Запустите сервер:
- Для Windows: startup.bat
- Для Linux/Mac: ./startup.sh
### 5) Откройте браузер и перейдите по адресу: http://localhost:8080.
Если вы видите главную страницу Tomcat, сервер работает.
## 3. Деплой вашего приложения
**Чтобы развернуть ваш WAR-файл:**

### 1) Скопируйте файл homework082.war (из папки target) в папку webapps внутри директории Tomcat.
Пример пути: C:\apache-tomcat-9.0.x\webapps.
### 2) Tomcat автоматически развернёт приложение. Вы можете наблюдать процесс в логах:
Путь к логам: C:\apache-tomcat-9.0.x\logs\catalina.out.
### 3) Перейдите в браузере по адресу:

```url
http://localhost:8080/homework082
```
## 4. Тестирование приложения
После выполнения вышеуказанных шагов ваше ToDo-приложение будет доступно в браузере. Убедитесь, что:

Вы видите интерфейс с полем ввода и кнопкой.
Можно добавлять задачи, отмечать их выполнение и удалять.
## 5. Дополнительно: автоматический деплой (опционально)
Если вы планируете разрабатывать и часто обновлять приложение, вместо ручного копирования WAR можно настроить автоматический деплой:

Добавьте плагин Tomcat в pom.xml:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.tomcat.maven</groupId>
            <artifactId>tomcat7-maven-plugin</artifactId>
            <version>2.2</version>
            <configuration>
                <url>http://localhost:8080/manager/text</url>
                <server>TomcatServer</server>
                <path>/homework082</path>
            </configuration>
        </plugin>
    </plugins>
</build>
```
### Настройте Tomcat для удалённого деплоя:

В файле conf/tomcat-users.xml добавьте:
```xml
<role rolename="manager-script"/>
<user username="admin" password="admin" roles="manager-script"/>
```
Выполните команду для деплоя:

```bash
mvn tomcat7:deploy
```
Теперь проект будет автоматически развернут на Tomcat после команды.

## 6. Остановка сервера
Если вам нужно остановить Tomcat:

Перейдите в папку bin.
Выполните:
- Для Windows: shutdown.bat
- Для Linux/Mac: ./shutdown.sh
