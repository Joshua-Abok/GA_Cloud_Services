# GA_Cloud_Services

This repository contains a Python project for GA Cloud Services. The project is configured with a Makefile to streamline various development tasks such as installing dependencies, linting, and running tests. Additionally, it includes a GitHub Actions workflow for continuous integration.

## Project Structure


- `.github/workflows/main.yml`: GitHub Actions workflow configuration.
- `.coverage`: Coverage report file.
- `.gitignore`: Specifies files and directories to be ignored by git.
- `hello.py`: Main Python script.
- `Makefile`: Makefile containing commands for installing dependencies, linting, and testing.
- `README.md`: This README file.
- `requirements.txt`: List of Python dependencies.
- `test_hello.py`: Unit test for `hello.py`.

## Prerequisites

- Python 3.10.14
- `pip` (Python package installer)
- `make` (build automation tool)

## Installation, Linting, and Testing

This command will sequentially execute the following steps:

1. `Upgrade pip` and `install all dependencies` specified in `requirements.txt`.
2. `Lint the code using pylint` with specific options to disable certain warnings and messages (R, C) for the hello.py file.
3. `Run the tests with pytest` and generate a coverage report for the hello.py file.

To install the required dependencies, lint the code, and run the tests, run the command:

```sh
make target
```

## Makefile changed 

```bash
target: install lint test

install: 
	pip install --upgrade pip && pip install -r requirements.txt

lint: 
	pylint --disable=R,C hello.py

test: 
	python -m pytest -vv --cov=hello test_hello.py
```

## Continuous Integration
The project is configured with GitHub Actions for continuous integration. The workflow is defined in `.github/workflows/main.yml` and is **triggered** on every push to the repository.

### Workflow Steps

#### Checkout the repository:

```bash 
- uses: actions/checkout@v2
```

#### Set up Python 3.10.14:
```bash 
- name: Set up Python 3.10.14
  uses: actions/setup-python@v1
  with:
    python-version: 3.10.14
```

#### Install dependencies lint, and test:
```bash 
- name: Install dependencies, Lint, and Test
  run: |
    make target
```

The workflow ensures that on every push, the code is checked out, the Python environment is set up, dependencies are installed, the code is linted, and the tests are executed.

## License
This project is licensed under the MIT License. See the LICENSE file for details.


This README file provides an overview of the project, explains how to install dependencies, run linting and tests, and describes the GitHub Actions workflow for continuous integration.

