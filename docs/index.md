---
layout: default
title: "Home"
---

# Prompter IDE Quick Start

Welcome to Prompter IDE, a plugin designed to bridge the gap between LLM (Large Language Model) chat services and your local file system. This allows you to bring context directly to your LLM, enabling quick reviews and decisions on changes to accept. Here’s how to get started.


<iframe width="560" height="315" src="https://www.youtube.com/embed/kpwF5hXLi3M" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---

### Overview of Prompter IDE

Prompter IDE connects an LLM with your local file system, making it easy to bring context into LLM conversations. This helps you make informed decisions about the changes proposed by the LLM by allowing you to review and control these changes within your project.

---

### Steps to Get Started

1. **Install the Plugin**
   [Install Prompter IDE](https://chromewebstore.google.com/detail/prompter-ide/chiamapkmadbnnfgkkipkeojnfofjfba) from the Chrome Web Store.

2. **Configure Extension Sites**
   Before using the extension, add the sites where you want it to be active in the extension options.
   - Go to the extension settings.
   - Enable it.
   - Specify the sites (one per line) to ensure Prompter IDE functions where needed.

3. **Plugin Sections**
   The plugin consists of various sections designed to handle prompts, manage files, and review history, all configured to work seamlessly with your LLM.

4. **Docker Installation**
   Ensure Docker is installed on your system, as it’s essential for running the plugin server.

---

### macOS/Linux Setup

If you are on macOS or Linux, follow these steps to set up Prompter IDE:

1. **Create Necessary Directories**
   Open your terminal and run the following command:
   ```bash
   mkdir -p ~/.prompter-ide/{history,prompts}
   ```

   This will create:
   - `~/.prompter-ide/history`: A directory to store internal version control history.
   - `~/.prompter-ide/prompts`: A directory to store saved prompts and snippets.

2. **Run the Plugin Using Docker**
   Start the Prompter IDE server with the following command:
   ```bash
   docker run -d \
     --name promter-ide-server \
     --restart always \
     -e API_SECRET=secret \
     -v "$(pwd):/usr/projects" \
     -v "$HOME/.prompter-ide/prompts:/usr/prompts" \
     -v "$HOME/.prompter-ide/history:/usr/history" \
     -v /var/run/docker.sock:/var/run/docker.sock \
     -p 8033:8030 \
     chaimvaid/prompter-ide-server
   ```

---

### Windows Setup

If you are on Windows, follow these steps:

1. **Create Necessary Directories**
   Open PowerShell and run the following commands:
   ```powershell
   mkdir -p "$HOME\.prompter-ide\history"
   mkdir -p "$HOME\.prompter-ide\prompts"
   ```

2. **Run the Plugin Using Docker**
   Update the volume mapping in the Docker command to use Windows paths. For example:
   ```powershell
   docker run -d `
     --name promter-ide-server `
     --restart always `
     -e API_SECRET=secret `
     -v C:\Users\<your-username>\.prompter-ide\prompts:/usr/prompts `
     -v C:\Users\<your-username>\.prompter-ide\history:/usr/history `
     -v C:\path\to\your\projects:/usr/projects `
     -v \\.\pipe\docker_engine:\\.\pipe\docker_engine `
     -p 8033:8030 `
     chaimvaid/prompter-ide-server
   ```

    Replace:
   - `<your-username>` with your Windows username.
   - `C:\path\to\your\projects` with the full path to your projects directory.

   
---

### Server Parameters

- **API_SECRET**: Set an API secret to secure access.
- **Mount Directories**:
  - `/usr/projects`: This should be the project directory you grant access to.
  - `/usr/prompts`: Contains saved prompts and snippets for persistence (optional).
  - `/usr/history`: Used for internal version control, allowing you to track changes and persist data.
  - `/var/run/docker.sock`: Optional, grants access to other Docker containers from within the server.

---

With these steps, your Prompter IDE is now set up and ready for use. Continue to explore the plugin sections for more advanced configurations and options.

---