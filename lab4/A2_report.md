# Отчёт по заданию A2: Vault ID

## 1. Что такое vault_id и зачем он нужен?
Vault ID — механизм Ansible для использования разных паролей для шифрования разных файлов. Формат: label@password_source, где label — метка окружения (dev, prod), password_source — файл с паролем.

## 2. Почему нельзя использовать один vault-пароль для всех окружений?
Компрометация одного пароля = компрометация всех окружений. Нарушается принцип разделения обязанностей. Разработчики не должны иметь доступ к prod-паролям.

## 3. Как передать несколько vault-паролей в GitLab CI?
Использовать защищённые переменные:
- echo "$DEV_VAULT_PASSWORD" > .vault_pass_dev
- echo "$PROD_VAULT_PASSWORD" > .vault_pass_prod
- ansible-playbook deploy.yml --vault-id dev@.vault_pass_dev --vault-id prod@.vault_pass_prod

## 4. Что произойдёт при неправильном vault-пароле?
Ansible выдаст ошибку: "Decryption failed on secrets.yml". Нужно проверить правильность пароля и соответствие vault-id.

## 5. Почему .vault_pass_* добавлены в .gitignore?
Если vault-пароль попадёт в Git, все зашифрованные секреты станут бесполезными. Злоумышленник расшифрует их за секунды.
