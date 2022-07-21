# Poetry Cookiecutter

A modern [Cookiecutter](https://github.com/cookiecutter/cookiecutter) template for scaffolding Python packages and apps.

## 🍿 Demo

See [My Package](https://github.com/radix-ai/my-package) for an example of a Python package and app that is scaffolded with this template.

Starting development in My Package is as easy as cloning the repository with `git clone git@github.com:radix-ai/my-package`, opening the cloned repository in [VS Code](https://code.visualstudio.com/) and then running <kbd>⌘</kbd> + <kbd>⇧</kbd> + <kbd>P</kbd> → _Remote-Containers: Reopen in Container_ with VS Code's [Remote-Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) to start a [Dev Container](https://code.visualstudio.com/docs/remote/containers).

## 🎁 Features

- 🧑‍💻 Quick and reproducible development environments with VS Code's [Dev Containers](https://code.visualstudio.com/docs/remote/containers) and PyCharm's [Docker Compose interpreter](https://www.jetbrains.com/help/pycharm/using-docker-compose-as-a-remote-interpreter.html#docker-compose-remote)
- 🌈 Cross-platform support for Linux, macOS (Apple silicon and Intel), and Windows
- 🐚 Modern shell prompt with [Starship](https://github.com/starship/starship)
- 📦 Packaging and dependency management with [Poetry](https://github.com/python-poetry/poetry)
- 🚚 Installing from and publishing to private package repositories and [PyPI](https://pypi.org/)
- ⚡️ Task running with [Poe the Poet](https://github.com/nat-n/poethepoet)
- ✍️ Code formatting with [black](https://github.com/psf/black) and [isort](https://github.com/PyCQA/isort)
- ✅ Code linting with [pre-commit](https://pre-commit.com/): [bandit](https://github.com/PyCQA/bandit), [darglint](https://github.com/terrencepreilly/darglint), [flake8](https://github.com/PyCQA/flake8), [mypy](https://github.com/python/mypy), [pre-commit-hooks](https://github.com/pre-commit/pre-commit-hooks), [pydocstyle](https://github.com/PyCQA/pydocstyle), [pygrep-hooks](https://github.com/pre-commit/pygrep-hooks), [pyupgrade](https://github.com/asottile/pyupgrade), [safety](https://github.com/pyupio/safety), and [shellcheck](https://github.com/koalaman/shellcheck)
- 🏷 Follows the [Conventional Commits](https://www.conventionalcommits.org/) standard to automate [Semantic Versioning](https://semver.org/) and [Keep A Changelog](https://keepachangelog.com/) with [Commitizen](https://github.com/commitizen-tools/commitizen)
- 💌 Verified commits with [GPG](https://gnupg.org/)
- ♻️ Continuous integration with [GitHub Actions](https://docs.github.com/en/actions) or [GitLab CI/CD](https://docs.gitlab.com/ee/ci/)
- 🧪 Test coverage with [Coverage.py](https://github.com/nedbat/coveragepy)
- 🏗 Scaffolding updates with [Cookiecutter](https://github.com/cookiecutter/cookiecutter) and [Cruft](https://github.com/cruft/cruft)
- 🧰 Dependency updates with [Dependabot](https://docs.github.com/en/code-security/supply-chain-security/keeping-your-dependencies-updated-automatically/about-dependabot-version-updates)

## ✨ Using

### Creating a new Python project

To create a new Python project with this template:
1. Install [Cruft](https://github.com/cruft/cruft) in your [Python environment](https://github.com/pyenv/pyenv-virtualenv) with:
   ```sh
   pip install cruft
   ```
2. Create a new repository and clone it locally.
3. In the repository's parent directory, run:
   ```sh
   cruft create -f git@github.com:radix-ai/poetry-cookiecutter
   ```

### Updating your Python project

To update your Python project with the latest template:
1. Run `cruft update` to update your project with the latest template.
2. If any of the updates failed, resolve them by inspecting the generated `.rej` files.

## 🤓 Template parameters

| Parameter                                                                           | Description                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `package_name`                    <br> "Spline Reticulator"                         | The name of the package. Will be slugified to snake_case for importing and kebab-case for installing.                                                                                                                                                                                                                                                                                                   |
| `package_description`             <br> "A Python package that reticulates splines." | A single-line description of the package.                                                                                                                                                                                                                                                                                                                                                               |
| `package_url`                     <br> "https://github.com/user/spline-reticulator" | The URL to the package's repository.                                                                                                                                                                                                                                                                                                                                                                    |
| `author_name`                     <br> "John Smith"                                 | The full name of the primary author of the package.                                                                                                                                                                                                                                                                                                                                                     |
| `author_email`                    <br> "john@example.com"                           | The email address of the primary author of the package.                                                                                                                                                                                                                                                                                                                                                 |
| `python_version`                  <br> "3.10"                                       | The minimum Python version that the package requires.                                                                                                                                                                                                                                                                                                                                                   |
| `with_fastapi_api`                <br> ["0", "1"]                                   | If "1", [FastAPI](https://github.com/tiangolo/fastapi) is added as a run time dependency, FastAPI API stubs and tests are added, `poe` commands for serving the API are added, and an `app` stage is added to the Dockerfile that packages the API. Additionally, the CI workflow will push the application as a Docker image instead of publishing the Python package.                                 |
| `with_jupyter_lab`                <br> ["0", "1"]                                   | If "1", [JupyterLab](https://github.com/jupyterlab/jupyterlab) is added to Poetry's dev dependencies, and a `poe lab` command is added to start Jupyter Lab in the `notebooks/` directory.                                                                                                                                                                                                              |
| `with_pydantic_typing`            <br> ["0", "1"]                                   | If "1", [Pydantic](https://github.com/samuelcolvin/pydantic) is added as a run time dependency, and the [Pydantic mypy plugin](https://pydantic-docs.helpmanual.io/mypy_plugin/) is enabled and configured.                                                                                                                                                                                             |
| `with_sentry_logging`             <br> ["0", "1"]                                   | If "1", [Sentry](https://github.com/getsentry/sentry-python) is added as a run time dependency, and a Sentry configuration stub and tests are added.                                                                                                                                                                                                                                                    |
| `with_streamlit_app`              <br> ["0", "1"]                                   | If "1", [Streamlit](https://github.com/streamlit/streamlit) is added as a run time dependency, a Streamlit application stub is added, a `poe streamlit` command is added to serve the Streamlit app, and an `app` stage is added to the Dockerfile that packages the Streamlit app. Additionally, the CI workflow will push the application as a Docker image instead of publishing the Python package. |
| `with_typer_cli`                  <br> ["0", "1"]                                   | If "1", [Typer](https://github.com/tiangolo/typer) is added as a run time dependency, Typer CLI stubs and tests are added, the package itself is registered as a CLI, and an `app` stage is added to the Dockerfile that packages the CLI.                                                                                                                                                              |
| `continuous_integration`          <br> ["GitHub", "GitLab"]                         | Whether to include a [GitHub Actions](https://docs.github.com/en/actions) or a [GitLab CI/CD](https://docs.gitlab.com/ee/ci/) continuous integration workflow for testing and publishing the package or app.                                                                                                                                                                                            |
| `docstring_style`                 <br> ["NumPy", "Google"]                          | Whether to use and validate [NumPy-style](https://numpydoc.readthedocs.io/en/latest/format.html) or [Google-style docstrings](https://google.github.io/styleguide/pyguide.html#38-comments-and-docstrings).                                                                                                                                                                                             |
| `private_package_repository_name` <br> "Private Package Repository"                 | Optional name of a private package repository to install packages from and publish this package to.                                                                                                                                                                                                                                                                                                     |
| `private_package_repository_url`  <br> "https://pypi.example.com/simple"            | Optional URL of a private package repository to install packages from and publish this package to. Make sure to include the `/simple` suffix.                                                                                                                                                                                                                                                           |
