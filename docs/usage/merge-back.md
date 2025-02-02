---
layout: default
title: "Merge Code Back to File System"
---

# Merge Code Back to File System

The "Merge Code Back" feature allows seamless integration of generated code from the LLM chat into the file system. This is facilitated via a slider interface that opens from the right side of the screen, providing two distinct tabs:

- **Select File**: Search and open an existing file from the file system.
- **Create New File**: Define a location, create folders or files, and save or edit their content.

---

## Workflow Scenarios

### Scenario 1: Pre-rendered Code in LLM Chat

If the LLM chat renders the generated code as a `<pre>` element:
1. A **folder icon** will be attached to each `<pre>` block.
2. Clicking the icon allows you to select a file from the file system. This opens a **diff view**:
   - **Left Side**: Displays the original file from the file system.
   - **Right Side**: Automatically loads the content from the `<pre>` block.
3. You can decide which changes to accept or ignore.
4. Click **Save** to update the file in the file system with the selected changes.

### Scenario 2: Non-pre-rendered Code in LLM Chat

If the LLM chat renders the generated code as an editor or in another form:
1. Copy the code you wish to merge.
2. Click on the **main file icon** (Prompter IDE circle).
3. The right side of the slider will initially be empty. Paste the copied code into the right side.
4. Proceed as in Scenario 1 to review, merge, and save the changes.

### Scenario 3: Context Menu Selection

In addition to the above workflows, you can use the **context menu** to insert selected content into the merge element:
1. Select the desired text from any document or code block.
2. Right-click to open the **context menu**.
3. Click **Open in Merge** to automatically insert the selection into the merge element.
4. From there, proceed as in the previous scenarios to merge and save the changes.

---

## Create Tab

The "Create New File" tab provides tools to:
- Search for a specific location in the file system.
- Create new folders or files.
- Edit or save the content directly.

### Additional Options:
1. **Pre-rendered Code**: Save the generated code directly without changes.
2. **Non-pre-rendered Code**: Click **Edit**, paste the code, and then save.

---

## Navigation

Return to [Prompt Editor](/usage/prompt.html) for more details on working with LLM-generated content.

