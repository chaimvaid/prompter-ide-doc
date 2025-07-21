---
layout: default
title: "Installation"
---

# Installation

## Requirements

- **Google Chrome** — for the browser extension.
- **Docker** — to run the Prompter IDE server.
- A supported LLM interface (e.g., ChatGPT).

## Steps

### 1. Install the Chrome Extension

[Install Prompter IDE](https://chromewebstore.google.com/detail/prompter-ide/chiamapkmadbnnfgkkipkeojnfofjfba) from the Chrome Web Store.

### 2. Configure Extension Sites

Before using the extension, add the sites where you want it to be active:

- Go to the extension settings.
- Enable the extension.
- Specify the allowed sites (one per line) where Prompter IDE should be active.

### 3. Set Up Docker

#### macOS/Linux

```bash
mkdir -p ~/.prompter-ide/{history,prompts}

docker run -d \
  --name promter-ide-server \
  --restart always \
  -e PROMPTER_DIR=/usr \
  -v "$HOME/.prompter-ide/prompts:/usr/prompts" \
  -v "$HOME/.prompter-ide/history:/usr/history" \
  -v /path/to/project-a:/usr/projects/project-a \
  -v /path/to/project-b:/usr/projects/project-b \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -p 8033:8030 \
  chaimvaid/prompter-ide-server ./main serve
````

#### Windows

```powershell
mkdir -p "$HOME\.prompter-ide\history"
mkdir -p "$HOME\.prompter-ide\prompts"

docker run -d `
  --name promter-ide-server `
  --restart always `
  -e PROMPTER_DIR=/usr `
  -v C:\Users\<your-username>\.prompter-ide\prompts:/usr/prompts `
  -v C:\Users\<your-username>\.prompter-ide\history:/usr/history `
  -v C:\path\to\project-a:/usr/projects/project-a `
  -v C:\path\to\project-b:/usr/projects/project-b `
  -v \\.\pipe\docker_engine:\\.\pipe\docker_engine `
  -p 8033:8030 `
  chaimvaid/prompter-ide-server ./main serve
```

> Replace `<your-username>` and the paths with your actual Windows username and project locations.

### 4. Set or Get API Secret

To retrieve the current API secret:

```bash
docker exec promter-ide-server sh -c 'PROMPTER_DIR=/usr ./main get-secret'
```

To set a new API secret:

```bash
docker exec promter-ide-server sh -c 'PROMPTER_DIR=/usr ./main set-secret <new-secret>'
```

---

## Server Parameters

* **`API_SECRET`**: Used to secure API access (recommended to change from the default).
* **Mount Directories**:

  * `/usr/projects`: Directory containing your code projects.
  * `/usr/prompts`: (Optional) Stores your saved prompts/snippets.
  * `/usr/history`: Internal Git-like history for prompt and file changes.
  * `/var/run/docker.sock`: (Optional) Enables the server to interact with other Docker containers.

---

Once everything is set up, you can begin using Prompter IDE. See the [UI Guide](#) for more details.

