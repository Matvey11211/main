# Отчёт по заданию B1: Ansible-коллекции

## 1. Что такое коллекция и чем отличается от роли?
Коллекция — формат дистрибуции контента, включающий роли, модули, плагины, документацию. Роль — структура каталогов для организации задач. Коллекция имеет namespace, версионирование, может распространяться через ansible-galaxy.

## 2. Что такое FQCN?
Fully Qualified Collection Name — полное квалифицированное имя: namespace.collection_name.resource_name. Пример: mystudent.sysadmin.nginx. Предотвращает конфликты имён.

## 3. Зачем нужен galaxy.yml?
Файл метаданных коллекции: namespace, name, version, authors, description, license, dependencies. Без него невозможно собрать и опубликовать коллекцию.

## 4. Как опубликовать коллекцию на Ansible Galaxy?
1. Создать аккаунт на galaxy.ansible.com
2. Сгенерировать API-токен
3. ansible-galaxy collection build mystudent/sysadmin
4. ansible-galaxy collection publish mystudent-sysadmin-1.0.0.tar.gz --api-key=ТОКЕН

## 5. Почему важно версионировать коллекции?
Гарантирует воспроизводимость, контроль изменений (breaking changes только в мажорных версиях), возможность отката, управление зависимостями.
