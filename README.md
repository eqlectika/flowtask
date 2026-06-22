# FlowTask Control & AI Worker

Система автоматизации задач на базе **GitHub Actions** и **Gemini API** с возможностью удаленного запуска через веб-интерфейс (**PWA**).

## 🛠 Архитектура системы

Проект состоит из трех основных компонентов:
1. **PWA Интерфейс (`index.html`)** — клиентское веб-приложение для ввода промпта и отправки `repository_dispatch` события в GitHub.
2. **Bash-скрипт** — автономный скрипт для локального тестирования или прямой отправки запросов к Gemini API.
3. **GitHub Workflow (`.github/workflows/ai-worker.yml`)** — автоматизация, которая принимает вебхук, обрабатывает текст через модель `gemini-1.5-flash` и сохраняет результат.

## 🚀 Настройка и развертывание

### 1. Секреты репозитория (Repository Secrets)
Для работы GitHub Actions необходимо добавить следующие переменные в `Settings -> Secrets and variables -> Actions`:
* `GEMINI_API_KEY` — ваш ключ доступа к API Google Gemini.
* `GH_TOKEN_PAT` — Personal Access Token (классический или fine-grained) с правами `contents: write` для записи результатов в репозиторий.

### 2. Настройка PWA Клиента
В файле `index.html` замените заглушку на ваш реальный токен GitHub в заголовке авторизации:
```javascript
'Authorization': 'token ВАШ_ТОКЕН_GITHUB'
