FROM python:3.13.16-slim

#copying uv from another docker image
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/ 

#current directory
WORKDIR /code 
ENV PATH="/code/.venv/bin:$PATH"

#copying existing uv to current directory?
COPY pyproject.toml .python-version  uv.lock ./ 

RUN uv sync --locked --no-install-project

#copying from host machine

COPY pipeline.py . 

ENTRYPOINT [ "python", "pipeline.py"]