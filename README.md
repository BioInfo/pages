# Multi-Site GitHub Pages Repository

This repository hosts multiple static websites using GitHub Pages. Each subdirectory within this repository represents a distinct website or project.

## Purpose

The primary goal is to provide a simple way to host and manage several small web projects or pages under a single GitHub repository, leveraging GitHub Pages for automatic deployment.

## Structure

-   **Root Directory:** Contains this `README.md` and the main `index.html`.
-   **`index.html` (Root):** Acts as a directory, listing and linking to all the individual sites hosted in the subdirectories.
-   **Subdirectories (e.g., `/bladder/`, `/prompt-pilot/`):** Each subdirectory contains the files for a specific website. The entry point for each site should be an `index.html` file within its respective directory.

## Deployment

GitHub Pages is configured to serve from the `main` branch of this repository. Any changes pushed to `main` will automatically trigger a deployment:
-   The root `index.html` is served at `https://[your-username].github.io/[repository-name]/`.
-   Each subdirectory site is served at `https://[your-username].github.io/[repository-name]/[subdirectory-name]/`.

## Contribution Guide for AI Agents (like Roo)

When asked to add a new site or project to this repository, follow these steps:

1.  **Create a New Directory:**
    -   Choose a concise, descriptive, lowercase name for the new site (e.g., `new-cool-site`).
    -   Use the `write_to_file` tool to create the site's main file (e.g., `write_to_file` with path `new-cool-site/index.html` and the site's HTML content). Add any other necessary assets (CSS, JS, images) into this directory using `write_to_file`.

2.  **Update the Root Directory (`index.html`):**
    -   **Read:** Use the `read_file` tool to get the current content of the root `index.html`.
    -   **Identify Insertion Point:** Locate the comment `<!-- Add new site entries here -->`.
    -   **Prepare Content:** Create the HTML snippet for the new directory entry. It should look like this (replace `new-cool-site` and the description):
        ```html
        <li>
            <a href="./new-cool-site/">New Cool Site</a>
            <p>Description for the New Cool Site.</p>
        </li>
        ```
    -   **Insert:** Use the `insert_content` tool. Specify the `path` as `index.html`. Determine the correct `start_line` number (the line *before* the `<!-- Add new site entries here -->` comment). Provide the HTML snippet created above as the `content`. Ensure correct indentation.

3.  **Commit and Push:**
    -   Use `execute_command` to run `git add .`.
    -   Use `execute_command` to run `git commit -m "Add new site: [site-name]"`.
    -   Use `execute_command` to run `git push origin main`.

**Example `insert_content` usage (line number is hypothetical):**

```xml
<insert_content>
<path>index.html</path>
<operations>[
  {
    "start_line": 26,
    "content": "        <li>\n            <a href=\"./new-cool-site/\">New Cool Site</a>\n            <p>Description for the New Cool Site.</p>\n        </li>"
  }
]</operations>
</insert_content>
```

By following these steps, new sites can be added consistently, and the main directory will be kept up-to-date, triggering automatic deployment via GitHub Pages.