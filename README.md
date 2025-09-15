# Tutorial

This tutorial shows you how to create a new project ready for development.

### Step 1: Install `uv`

Install [`uv`](https://docs.astral.sh/uv/#getting-started) to manage Python environments and dependencies. Once installed, you can quickly create isolated environments for your projects.

For macOS, run:

```
$ curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Step 2: Generate your project

This step will create a new project folder with all the necessary files. Replace `<template_path>` with the path to your cookiecutter template.

```
$ cd <new_project_folder>  # go into the folder you want to generate the project in
$ uv venv --python 3.13
$ uv pip install cookiecutter
$ uv run cookiecutter <template_path>
```

### Step 3: Initialize Git

Replace `<project_name>` with the name of your generated project.

```
$ cd <project_name>
$ git init
```

### Step 4: Set Up Development Environment

Prepare the environment and install pre-commit hooks:

```
$ make install
```

This will generate the `uv.lock` file.

### Step 5: Run the pre-commit hooks

For the first time, run all pre-commit hooks to generate the `requirements.txt` file and ensure code quality:

```
$ make check
```
