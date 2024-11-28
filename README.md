# eBook Development Template for VS Code

This repository provides a structured template for writing and organizing an eBook using **Markdown** in **Visual Studio Code** (VS Code). It includes tools for generating a Table of Contents (TOC), exporting to various formats (PDF, EPUB), and ensuring a clean and organized workflow.

## Features

- **Organized Directory Structure**: Keep chapters, assets, and metadata neatly separated.
- **Markdown Support**: Write your content in Markdown for simplicity and flexibility.
- **Automatic TOC Generation**: Generate a dynamic Table of Contents linking to chapter headers.
- **Export Formats**: Convert your ebook to PDF and EPUB using pandoc.
- **Styling: Customize your eBook with CSS for consistent formatting.
- **Automation**: Predefined tasks for exporting and validating eBook files.

## Prerequisites

Before using this eBook development setup, ensure the following dependencies are installed on your system.

### Required Tools

| Dependency | Description | Installation Command/Linux |
|------------|-------------|----------------------------|
| **Pandoc** | Converts Markdown to EPUB/PDF and other formats.| sudo apt install pandoc |
| **LaTeX (XeLaTeX)** | Required for PDF export with Pandoc.| sudo apt install texlive-xetex |
| **Calibre** (Optional)| eBook reader and validation tool for EPUB. | sudo apt install calibre |
| **Python 3** | Needed to run the Table of Contents generator script. | sudo apt install python3 |
| **Java** (Optional) | Required for `epubcheck` to validate EPUB files. | sudo apt install default-jre |
| **Okular** (Optional) | Lightweight document viewer for EPUB/PDF. | sudo apt install okular |
| **Git** | Version control | sudo apt install git |

### Extensions

Recommended extensions for VS Code:

- **Code Spell Checker**: Spell checker.
- **Markdown All in One**: Markdown support and TOC generation.
- **Markdownlint**: A linting and style guide.
- **Markdown Preview Enhanced**: Enhanced Markdown preview.
- **Python**:  Enables Python scripting support.
- **YAML**: Language extension for metadata file.

## Directory Structure

```plain text
eBook_Project/
├── .vscode/              # VS Code-specific configurations
│   └── tasks.json        # Tasks for exporting to PDF and EPUB
├── chapters/             # Individual chapter files
│   ├── 01-introduction.md
│   ├── 02-background.md
│   └── ...
├── assets/               # Images, figures, and other media
│   └── images
│    └── cover.webp        # Cover image for the eBook
├── metadata/             # Metadata files
│   ├── frontmatter.md    # Metadata template for use in Markdown files. 
│   ├── ebook.yaml        # YAML frontmatter metadata
├── styles/               
│   └── custom.css        # CSS for EPUB styling
├── output/               # Exported eBook files
│   ├── ebook.pdf
│   └── ebook.epub
└── README.md             # Project documentation (this file)
```

## Getting Started

### Step 1: Install Required Tools

Ensure the following are installed on your system:

- Linux (Ubuntu/Debian)
  - Run the following commands to install all required tools:

    ```bash

    # Install Pandoc
    sudo apt update
    sudo apt install pandoc

    # Install LaTeX (XeLaTeX for PDF export)
    sudo apt install texlive-xetex

    # Install Calibre for EPUB validation and reading
    sudo apt install calibre

    # Install Python 3
    sudo apt install python3 python3-pip

    # (Optional) Install Java for epubcheck validation
    sudo apt install default-jre

    # (Optional) Install Okular for EPUB/PDF viewing
    sudo apt install okular
    ```

- Windows

  - **Pandoc**: Download and install from the official website.
  - **LaTeX**: Install MikTeX.
  - **Calibre**: Download from calibre-ebook.com.
  - **Python**: Install from the official website.
  - **Java** (Optional): Install the JRE from Oracle or OpenJDK.
  - **Okular** (Optional): Download from the Okular website.

- macOS
  - Use brew (Homebrew) to install the required tools:

    ```bash
    # Install Pandoc
    brew install pandoc

    # Install LaTeX (MacTeX)
    brew install --cask mactex

    # Install Calibre
    brew install --cask calibre

    # Install Python 3
    brew install python

    # (Optional) Install Java for epubcheck validation
    brew install --cask temurin

    # (Optional) Install Okular
    brew install --cask okular
    ```

### Step 2: Validating Dependencies

To confirm that the required dependencies are installed and working, run the following commands:

- Pandoc:

```bash
pandoc --version
```

- LaTeX (XeLaTeX):

```bash
xelatex --version
```

- Calibre:

```bash
calibre --version
```

- Python:

```bash
python3 --version
```

- Java (Optional for epubcheck):

```bash
java -version
```

### Step 3: Set Up the Workspace

- Clone this template to your local machine:

    ``` bash
    git clone <repository-url> eBook_Project
    cd eBook_Project
    ```

- Open the folder in VS Code:

    ```bash
    code .
    ```

### Step 4: Customize Metadata

Edit the `metadata/frontmatter.md` (example of chapter YAML headers) or `metadata/ebook.yaml` (eBook details) files to include your book's title, author, and other metadata:

#### Markdown `frontmatter.md' Header

```yaml
---
title: "Chapter Title"
contributors:
  - "Editor: Your Name"
  - "Reviewer: Contributor Name"
keywords:
  - example
  - placeholder
---
```

#### eBook YAML:

```yaml
title: "My eBook Title"
author: "Your Name"
date: "2024-11-23"
cover-image: "assets/images/cover.webp"
language: "en"
```

### Step 5: Write Your Content

- Add chapters in the chapters/ directory as separate Markdown files.
- Use headers (#, ##, etc.) to structure the content, enabling automatic TOC generation.

### Step 6: Export Your eBook

Use VS Code's preconfigured tasks to export to PDF or EPUB:

- Press Ctrl+Shift+B to run the default Export to PDF task.
- Alternatively, run the Export to EPUB task:

    ```bash
    pandoc --toc -o output/ebook.epub metadata/frontmatter.md chapters/*.md
    ```

## Customizing the Template

### Styling with CSS

Modify the `styles/custom.css` file to define styles for your eBook (EPUB only):

```css
body {
    font-family: Georgia, serif;
    line-height: 1.6;
}
h1, h2, h3 {
    color: #4A90E2;
}
```

### Cover Image

Replace `assets/images/cover.webp` with your own cover image.

## Validation and Preview

### Validate EPUB

Use `epubcheck` to validate your EPUB.

```bash
java -jar epubcheck.jar output/ebook.epub
```

### Preview eBook

- **PDF**: Open with any PDF viewer.
- **EPUB**: Use Calibre or Okular:

    ```bash
    okular output/ebook.epub
    ```

## Automation with VS Code

The `.vscode/tasks.json` file includes preconfigured tasks for exporting to PDF and EPUB:

```json
{
  "label": "Export to PDF",
  "type": "shell",
  "command": "pandoc",
  "args": [
    "--pdf-engine=xelatex",
    "--toc",
    "-o",
    "output/ebook.pdf",
    "metadata/frontmatter.md",
    "chapters/*.md"
  ]
}
```

## Setting Up Optional Version Control with Git

Tracking changes in your eBook project is  essential for maintaining a history of edits, collaborating with others, and safely managing your content. Follow these steps to enable Git in your project:

### Install Git

Before starting, ensure Git is installed on you system:

- **Linux** (Ubuntu/Debain):

    ```bash
    sudo apt install git
    ```

- **Windows**: Download and install Git from [hit-scm.com](git-scm.com).
- **MacOS**: Install Git using HomeBrew:

    ```bash
    brew install git
    ```

Verify the installation:

```bash
git --version
```

### Initialize a Git Repository

- Open a terminal in the root directory of your project:
  
   ```bash
   cd eBook-Project
   ```

- Initialize the Git repository:

    ```bash
    git init
    ```

- Add all files to the staging area:

    ```bash
    git add .
    ```

- Commit the initial version of your project:

    ```bash
    git commit -m "Initial commit: Set up eBook project template"
    ```

### Configure `.gitignore`

Prevent certain files and folders from being tracked by Git. Create a `.gitignore` file in the project root with the following content:

```plaintext
# Ignore VS Code configurations
.vscode/

# Ignore output files
output/

# Ignore temporary or backup files
*.log
*.tmp
*.bak

# Ignore system files
.DS_Store
```

Add the `.gitignore` to Git and commit it:

```bash
git add .gitignore
git commit -m "Add .gitignore file"
```

### Connect to a Remote Repository (Optional)

If you want to back up your project or to collaborate, push it to a remote Git repository (e.g., GitHub, GitLab).

- Create a new repository on GitHub or your preferred platform.
- Link your local repository to the remote:

```bash
git remote add origin <your-repository-url>
```

- Push your local changes to the remote repository:

```bash
git branch -M main
git push -u origin main
```

### Track Changes

As you work on your eBook, track changes using Git commands:

- Check the status of your repository:

    ```bash
    git status
    ```

- Stage modified files:

    ```bash
    git add <file>
    ```

- Commit changes with a meaningful message:

    ```bash
    git commit -m "Update chapter 1 content"
    ```

- Push changes to the remote repository:

    ```bash
    git push
    ```

### View Version History

To review your project's change history:

``` git log
```

### Roll Back Changes (Optional)

If you do make a mistake and want to revert to a previous version, use:

- Undo changes in the working directory:

    ```bash
    git checkout -- <file>
     ```

- Revert to a previous commit:

    ```bash
    git reset --hard <commit-hash>
    ```

You can find `<commit-hash>` by running `git log`.

## Contributing

Contributions are welcome! Feel free to fork this template, make improvements, and submit a pull request.

## License

This template is provided under the MIT License. Feel free to use and modify it for your projects.
