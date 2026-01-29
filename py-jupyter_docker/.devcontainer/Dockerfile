FROM python:3.11-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app

RUN pip install --no-cache-dir --upgrade pip \
 && pip install --no-cache-dir jupyter

# Create a small startup script (more reliable than a long CMD array)
RUN printf '%s\n' \
'#!/bin/sh' \
'set -e' \
'jupyter notebook --ip=0.0.0.0 --port=8888 --no-browser --allow-root --NotebookApp.token= --NotebookApp.password=' \
> /usr/local/bin/start-jupyter.sh \
&& chmod +x /usr/local/bin/start-jupyter.sh

EXPOSE 8888

CMD ["/usr/local/bin/start-jupyter.sh"]