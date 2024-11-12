---
layout: default
title: "Home"
---


Here’s an improved version of the **Quick Start** page based on your prompt:

---

# Quick Start

Welcome to Prompter IDE, a plugin designed to bridge the gap between LLM (Large Language Model) chat services and your local file system. This allows you to bring context directly to your LLM, enabling quick reviews and decisions on changes to accept. Here’s how to get started.

### Overview of Prompter IDE

Prompter IDE is a plugin that connects an LLM with your local file system, making it easy to bring context into LLM conversations. This helps you make informed decisions about the changes proposed by the LLM by allowing you to review and control these changes within your project.

### Steps to Get Started

1. **Install the Plugin**: Follow the installation instructions to get Prompter IDE set up as a plugin within your system.

2. **Plugin Sections**: The plugin consists of various sections designed to handle prompts, manage files, and review history, all of which are configured to work seamlessly with your LLM.

3. **Docker Installation**: Ensure Docker is installed on your system, as it’s essential for running the plugin server.

4. **Run the Plugin Using Docker**: Prompter IDE requires a Docker-based server to enable file system access. Use the Docker command below to run the plugin:

    ```bash
    docker run -d \
      --name promter-ide-server \
      --restart always \
      -e API_SECRET=secret \
      -v "$(pwd):/usr/projects" \
      -v "$(pwd)/prompts:/usr/prompts" \
      -v "$(pwd)/history:/usr/history" \
      -v /var/run/docker.sock:/var/run/docker.sock \
      -p 8033:8030 \
      chaimvaid/prompter-ide-server
    ```

5. **Server Parameters**: Configure the server parameters as follows:
   - **API_SECRET**: Set an API secret to secure access.
   - **Mount Directories**:
     - `/usr/projects`: This should be the project directory you grant access to.
     - `/usr/prompts`: Contains saved prompts and snippets for persistence (optional).
     - `/usr/history`: Used for internal version control, allowing you to track changes and persist data (optional).
     - `/var/run/docker.sock`: Optional, grants access to other Docker containers from within the server.

With these steps, your Prompter IDE is now set up and ready for use. Continue to explore the plugin sections for more advanced configurations and options.