# {{ cookiecutter.package_name }}

{{ cookiecutter.package_description }}

## Using

To add and install this package as a dependency of your project, run `poetry add {{ cookiecutter.package_name|slugify }}`.
{%- if cookiecutter.with_typer_cli|int %}

To view this app's commands once it's installed, run `{{ cookiecutter.package_name|slugify }} --help`. Alternatively, you can also use `docker compose run --rm app --help`.
{%- endif %}
{%- if cookiecutter.with_fastapi_api|int or cookiecutter.with_streamlit_app|int %}

To serve this app, run `docker compose up app` and open [localhost:8000](http://localhost:8000) in your browser. Within the Dev Container, this is equivalent to running {% if cookiecutter.with_fastapi_api|int %}`poe serve`{% else %}`poe streamlit`{% endif %}.
{%- endif %}

## Contributing

<details>
<summary>Setup: once per device</summary>

{% if cookiecutter.continuous_integration == "GitLab" -%}
1. [Generate an SSH key](https://docs.gitlab.com/ee/ssh/README.html#generate-an-ssh-key-pair) and [add the SSH key to your GitLab account](https://docs.gitlab.com/ee/ssh/README.html#add-an-ssh-key-to-your-gitlab-account).
1. Configure SSH to automatically load your SSH keys:
    ```sh
    cat << EOF >> ~/.ssh/config
    Host *
      AddKeysToAgent yes
      IgnoreUnknown UseKeychain
      UseKeychain yes
    EOF
    ```
{%- if cookiecutter.private_package_repository_name %}
1. [Create a personal access token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html#create-a-personal-access-token) with the `api` scope and use it to [add your private package repository credentials to your Poetry's `auth.toml` file](https://python-poetry.org/docs/repositories/#configuring-credentials):
    ```toml
    # Linux:   ~/.config/pypoetry/auth.toml
    # macOS:   ~/Library/Application Support/pypoetry/auth.toml
    # Windows: C:\Users\%USERNAME%\AppData\Roaming\pypoetry\auth.toml
    [http-basic.{{ cookiecutter.private_package_repository_name|slugify }}]
    username = "{personal access token name}"
    password = "{personal access token}"
    ```
{%- endif %}
{%- else -%}
1. [Generate an SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key) and [add the SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
1. Configure SSH to automatically load your SSH keys:
    ```sh
    cat << EOF >> ~/.ssh/config
    Host *
      AddKeysToAgent yes
      IgnoreUnknown UseKeychain
      UseKeychain yes
    EOF
    ```
{%- if cookiecutter.private_package_repository_name %}
1. [Add your private package repository credentials to your Poetry's `auth.toml` file](https://python-poetry.org/docs/repositories/#configuring-credentials):
    ```toml
    # Linux:   ~/.config/pypoetry/auth.toml
    # macOS:   ~/Library/Application Support/pypoetry/auth.toml
    # Windows: C:\Users\%USERNAME%\AppData\Roaming\pypoetry\auth.toml
    [http-basic.{{ cookiecutter.private_package_repository_name|slugify }}]
    username = "{username}"
    password = "{password}"
    ```
{%- endif %}
{%- endif %}
1. [Install Docker Desktop](https://www.docker.com/get-started).
    - Enable _Use Docker Compose V2_ in Docker Desktop's preferences window.
    - If you are using Linux, you must [configure Docker and Docker Compose to use the BuildKit build system](https://pythonspeed.com/articles/docker-buildkit/). On macOS and Windows, BuildKit is enabled by default in Docker Desktop.
1. [Install VS Code](https://code.visualstudio.com/) and [VS Code's Remote-Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers). Alternatively, install [PyCharm](https://www.jetbrains.com/pycharm/download/).
    - _Optional:_ Install a [Nerd Font](https://www.nerdfonts.com/font-downloads) such as [FiraCode Nerd Font](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/FiraCode) with `brew tap homebrew/cask-fonts && brew install --cask font-fira-code-nerd-font` and [configure VS Code](https://github.com/tonsky/FiraCode/wiki/VS-Code-Instructions) or [configure PyCharm](https://github.com/tonsky/FiraCode/wiki/Intellij-products-instructions) to use `'FiraCode Nerd Font'`.

</details>

<details open>
<summary>Setup: once per project</summary>

_Containerized development_:

1. Clone this repository.
{%- if cookiecutter.private_package_repository_name %}
1. Create a `.env` file in the project directory that [Docker Compose reads](https://docs.docker.com/compose/env-file/) to use Poetry's `auth.toml` file as a [build and run time secret](https://docs.docker.com/compose/compose-file/compose-file-v3/#secrets-configuration-reference):
    ```sh
    # Linux
    POETRY_AUTH_TOML_PATH="~/.config/pypoetry/auth.toml"

    # macOS
    POETRY_AUTH_TOML_PATH="~/Library/Application Support/pypoetry/auth.toml"

    # Windows
    POETRY_AUTH_TOML_PATH="$APPDATA/pypoetry/auth.toml"
    ```
{%- endif %}
1. Start a [Dev Container](https://code.visualstudio.com/docs/remote/containers) in your preferred development environment:
    - _VS Code_: open the cloned repository and run <kbd>⌘</kbd> + <kbd>⇧</kbd> + <kbd>P</kbd> → _Remote-Containers: Reopen in Container_.
    - _PyCharm_: open the cloned repository and [configure Docker Compose as a remote interpreter](https://www.jetbrains.com/help/pycharm/using-docker-compose-as-a-remote-interpreter.html#docker-compose-remote).
    - _Terminal_: open the cloned repository and run `docker compose run --rm dev` to start an interactive Dev Container.

_Local development_:

1. Clone this repository.
2. Install the Poetry environment with `poetry install`.
3. Activate your Poetry environment with `poetry shell`.
4. Install the pre-commit hooks with `pre-commit install --install-hooks`.

</details>

<details>
<summary>Developing</summary>

- This project follows the [Conventional Commits](https://www.conventionalcommits.org/) standard to automate [Semantic Versioning](https://semver.org/) and [Keep A Changelog](https://keepachangelog.com/) with [Commitizen](https://github.com/commitizen-tools/commitizen).
- Run `poe` from within the development environment to print a list of [Poe the Poet](https://github.com/nat-n/poethepoet) tasks available to run on this project.
- Run `poetry add {package}` from within the development environment to install a run time dependency and add it to `pyproject.toml` and `poetry.lock`.
- Run `poetry remove {package}` from within the development environment to uninstall a run time dependency and remove it from `pyproject.toml` and `poetry.lock`.
- Run `poetry update` from within the development environment to upgrade all dependencies to the latest versions allowed by `pyproject.toml`.
- Run `cz bump` to bump the package's version, update the `CHANGELOG.md`, and create a git tag.

</details>
