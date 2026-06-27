# FlowTask Control & AI Worker
A task automation system based on **GitHub Actions** and the **Gemini API**, featuring remote execution via a web interface (**PWA**).
## 🛠 System Architecture
The project consists of three core components:
 1. **PWA Interface (index.html)** — A client-side web application for inputting prompts and sending a repository_dispatch event to GitHub.
 2. **Bash Script** — A standalone script for local testing or direct requests to the Gemini API.
 3. **GitHub Workflow (.github/workflows/ai-worker.yml)** — An automation that receives the webhook, processes the text via the gemini-1.5-flash model, and saves the result.
## 🚀 Setup and Deployment
### 1. Repository Secrets
For GitHub Actions to function, add the following variables under Settings -> Secrets and variables -> Actions:
 * GEMINI_API_KEY — Your Google Gemini API access key.
 * GH_TOKEN_PAT — A Personal Access Token (classic or fine-grained) with contents: write permissions to commit results to the repository.
### 2. PWA Client Configuration
In index.html, replace the placeholder with your actual GitHub token in the authorization header:
```javascript
'Authorization': 'token YOUR_GITHUB_TOKEN'

```