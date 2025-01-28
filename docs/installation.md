---
layout: default
title: "Installation"
---

# Installation

## Requirements

- **Google Chrome** for the browser extension.
- **Docker** to run the Prompter IDE server.
- A supported LLM interface (e.g., ChatGPT).

## Steps

1. **Install the Chrome Extension**
   [Install Prompter IDE](https://chrome.google.com/webstore) from the Chrome Web Store.

2. **Configure Extension Sites**
   Before using the extension, add the sites where you want it to be active in the extension options.
   - Go to the extension settings.
   - Enable it.
   - Specify the sites (one per line) to ensure Prompter IDE functions where needed.

3. **Set Up Docker**

### macOS/Linux

```bash
mkdir -p ~/.prompter-ide/{history,prompts}

docker run -d \
  --name promter-ide-server \
  --restart always \
  -e API_SECRET=secret \
  -v "$HOME/.prompter-ide/prompts:/usr/prompts" \
  -v "$HOME/.prompter-ide/history:/usr/history" \
  -v /path/to/project-a:/usr/projects/project-a \
  -v /path/to/project-b:/usr/projects/project-b \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -p 8033:8030 \
  chaimvaid/prompter-ide-server
```

### Windows

```powershell
mkdir -p "$HOME\.prompter-ide\history"
mkdir -p "$HOME\.prompter-ide\prompts"

docker run -d `
  --name promter-ide-server `
  --restart always `
  -e API_SECRET=secret `
  -v C:\Users\<your-username>\.prompter-ide\prompts:/usr/prompts `
  -v C:\Users\<your-username>\.prompter-ide\history:/usr/history `
  -v C:\path\to\project-a:/usr/projects/project-a `
  -v C:\path\to\project-b:/usr/projects/project-b `
  -v \\.\pipe\docker_engine:\\.\pipe\docker_engine `
  -p 8033:8030 `
  chaimvaid/prompter-ide-server
```

Replace `<your-username>` and paths with your actual username and project paths.

Check the UI Guide once you’ve set everything up.

### Server Parameters

- **API_SECRET**: Set an API secret to secure access.
- **Mount Directories**:
  - `/usr/projects`: This should be the project directory you grant access to.
  - `/usr/prompts`: Contains saved prompts and snippets for persistence (optional).
  - `/usr/history`: Used for internal version control, allowing you to track changes and persist data.
  - `/var/run/docker.sock`: Optional, grants access to other Docker containers from within the server.
