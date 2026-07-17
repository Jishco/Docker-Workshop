FROM python:3.11-slim

RUN pip install pandas pyarrow
WORKDIR /app

ENV PATH="/app/.venv/bin:$PATH"

COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/
COPY pyproject.toml .python-version uv.lock ./
COPY pipeline.py pipeline.py

RUN uv sync --locked
#ENTRYPOINT ["bash"]
ENTRYPOINT ["python", "pipeline.py"]