---
layout: default
title: "Advanced Configuration"
---

# Advanced Configuration

Customize your Prompter IDE setup:

## Environment Variables

- `API_SECRET`: Protects access to the server. Set it in the `docker run` command.

## Docker Parameters

- `/usr/projects`: Mount your project directory here.
- `/usr/prompts`: Persistent storage for prompts/snippets.
- `/usr/history`: Internal version control storage.
- `/var/run/docker.sock`: Optional, enables Docker integrations.

For common issues, see the [FAQ](/faq.html).
