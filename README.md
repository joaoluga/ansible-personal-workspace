# Table of Contents
- [Description](#Description)
    - [Features](#features)
    - [Requirements](#requirements)
    - [Usage](#usage)
        - [Testing the Playbook](#testing-the-playbook)
        - [Applying Changes](#applying-changes)
    - [Customization](#customization)
        - [Modify Variables](#modify-variables)
        - [Add New Tasks](#add-new-tasks)
            - [Example](#example)


# Description
This repository contains an Ansible playbook designed to automate the setup of a local development workspace. It installs essential tools, packages, and environment configurations tailored to the user's preferences.

## Features

- Install packages using Homebrew.
- Configure Python environments with custom packages.
- Set up environment variables in the user's shell configuration (`.zshrc`, `.bashrc`, etc.).
- Fully customizable for additional tools and configurations.

## Requirements

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) installed on your system.
- macOS or a Unix-based system with Homebrew support.

## Usage

### Testing the Playbook

To test the playbook and preview changes without applying them, use:

```bash
ansible-playbook main.yml --check --diff
```
- check: Runs the playbook in "dry-run" mode to simulate changes.
- diff: Shows differences between the current and desired state.

### Applying Changes
To execute the playbook and apply the configurations:

```bash
ansible-playbook main.yml
```
## Customization
### Modify Variables
To customize your setup, edit the variables in the vars/main.yml file:

Homebrew packages: Add or remove packages to be installed.
Python packages: Define the list of Python packages to install.
Environment variables: Adjust variables to be added to your shell configuration file.

### Add New Tasks
To extend the playbook with additional configurations:
1. Create a new task file in the tasks directory.

```yaml
- name: <Task Name>
  <module_name>:
    <module_option>: <value>
```

2. Import the task into main.yml using the following syntax:

```yaml
- name: <Process Name>
  import_tasks: <task_file_name>.yml
```
#### Example

If you create a new file tasks/setup_docker.yml, you can include it in main.yml like this:

```yaml
- name: Docker Setup
  import_tasks: setup_docker.yml
```