# {{cookiecutter.project_name}}

{{cookiecutter.project_description}}

## Development

### Setup

Install [`uv`](https://docs.astral.sh/uv/#getting-started) to manage Python environments and dependencies. For macOS, run:

```
$ curl -LsSf https://astral.sh/uv/install.sh | sh
```

Set up the development environment and install pre-commit hooks:

```
$ make install
```

### Running

Start the FastAPI server locally:

```
$ make run
```

Run all pre-commit checks (linting, formatting, etc.) and also verify if `requirements.txt` needs updating.

```
$ make check
```

Swagger UI is available at [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs). You can use it to test the API endpoints and explore the API documentation.

## Deployment

Use Docker Compose to launch the whole backend stack. The following environments are available:

- development (`dev`)
- staging (`stage`)
- production (`prod`)

To start the whole stack, run:

```
$ make deploy env=dev
```

To take down the stack, run:

```
$ make down env=dev
```

To view logs for a specific service, use `logs-{service}`. You can also customize the number of log lines to display with the `log_lines` argument:

```
$ make logs-api env=dev log_lines=50
```
