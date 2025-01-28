---

layout: default
title: "Prompt Editor"
----------------------

# Prompt Editor

The Prompt Editor is the main workspace for interacting with epics, sections, and files, enabling seamless integration of snippets and files into your prompts.

---

## Overview

The Prompt Editor provides a rich text editing environment for managing epics and their sections, configuring snippets, and attaching files. This ensures a streamlined and efficient workflow for creating dynamic and reusable prompts.

---

## How It Works

### Step 1: Select an Epic

On the right-hand side of the page, you can select an epic to work with. This will load all sections and attached files related to the selected epic.

### Step 2: Edit Sections

In the center of the page, a rich text editor is available for each section of the selected epic. Each editor represents a single section, allowing you to:

- Type and organize content.
- Use snippets and attach files dynamically.

---

## Features

### Snippet Suggestions

You can configure snippets through the [Snippet Page](#) and use them while typing in the editor. When the typed word matches a snippet, a suggestion list will appear for quick insertion.

### Attaching Files

To attach a file:

- Type `@` followed by the file name, e.g., `@modal/modalname.php`.
- A suggestion list will appear for file selection.

Once a file is selected, the suggestion section on the left-hand side of the screen will display a list of files that have historically been associated with the selected file. Clicking on any file in the list will load it into the editor.

#### Managing Files in Epics

When creating or editing an epic, you can attach files to it. These files are displayed in the epic's "Files" section on the left-hand side of the screen. Clicking on a file in this section will:

1. Load the file into the editor as a placeholder.
2. Ensure the latest version of the file is loaded when you press the "Copy" button.

---

## Copying and Using Prompts

To use a prompt in an LLM's chat field:

1. Copy a section using the **Copy** button located above each section in the editor.
2. Close the Prompter IDE window.
3. Paste the copied content into the LLM's chat prompt field.

All attached files will be included in the copied content, ensuring the most updated versions are used.

---

## Navigation

Return to [Epics Section](/usage/epic.html) to learn more about managing epics.

