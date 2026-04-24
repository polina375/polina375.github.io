# Лабораторная работа 3:  Реализация автоматического развёртывания статического сайта на MkDocs с использованием Sourcecraft и GitHub Actions
[ soursecraft] (https://sourcecraft.dev/polinaandreevna375/demo1403)

## Цель работы
Реализовать два сценария автоматического развёртывания статического сайта, созданного на базе генератора MkDocs:

через платформу Sourcecraft;
через GitHub Actions. 
## Задание
. Выполненные действия

Создан один локальный репозиторий с проектом MkDocs (mkdocs.yml находится в корне проекта, содержимое сайта — в папке src/docs).

Добавлены два удалённых репозитория:
origin — [GitHub] (https://github.com/polina375/polina375.github.io.git)

sourcecraft — Sourcecraft

Настроен автоматический деплой на Sourcecraft путём пуша в remote sourcecraft.
Настроен автоматический деплой на GitHub Pages с помощью GitHub Actions.
Выполнены пуши в оба удалённых репозитория.
Сайт успешно развёрнут на двух платформах.

3. Организация репозитория


mkdocs.yml — основной конфигурационный файл (в корне)

src/docs/ — папка с markdown-файлами сайта

requirements.txt — зависимости проекта (mkdocs, mkdocs-material и др.)

.sourcecraft — конфигурационный файл для развёртывания на Sourcecraft

.github/workflows/deploy-mkdocs.yml — workflow для автоматического развёртывания через GitHub Actions

.gitignore — стандартный для MkDocs проекта

В репозитории одна основная ветка — main.

## Нюансы
Токен доступа – создаётся один раз и отображается только при создании; необходимо сохранить его в надёжном месте.

Файл .sourcecraft/sites.yaml должен быть в корне главной ветки (main) и содержать корректные путь к собранному сайту и имя ветки для публикации.

Триггер воркфлоу – в файле воркфлоу обязательно указывать on: push: branches: main, иначе автоматический запуск не произойдёт.

Конфликт веток – при рассинхронизации локальной и удалённой веток необходимо выполнить git pull --rebase или git push --force (только если вы уверены в своих изменениях).

Сборка в отдельную папку – рекомендуется собирать сайт в папку site (или другую, не занятую исходниками), чтобы не затирать исходные файлы.

## Что необходимо сделать для выполнения деплоя
Для деплоя на Sourcecraft:

Добавить remote:
git remote add sourcecraft https://<username>:<PAT>@git.sourcecraft.dev/<org>/<repo>.git

Создать файл .sourcecraft в корне

Для деплоя на GitHub Pages:

Создать файл .github/workflows/deploy-mkdocs.yml
Выполнить: git push origin main
Workflow запускается автоматически при пушe в main, либо вручную через кнопку «Run workflow».

Настройки, выполненные в репозиториях
В GitHub:

В разделе Settings → Pages:

Source → выбран GitHub Actions (а не Deploy from a branch)

В разделе Settings → Actions → General → Workflow permissions:

Установлено Read and write permissions для GitHub token


В Sourcecraft:

Создана публичная организация

Создан публичный репозиторий

Создан Personal Access Token (PAT) с правами Maintainer (сроком на 1 год)

Репозиторий добавлен как remote sourcecraft с использованием HTTPS + PAT

Выполнить команду:
git push sourcecraft main

git remote -v

## Вывод
В ходе лабораторной работы я изучила возможности платформы SourceCraft для хостинга и автоматического деплоя статических сайтов. Настроила CI/CD‑пайплайн, который собирает сайт с помощью MkDocs и публикует его в отдельной ветке. 