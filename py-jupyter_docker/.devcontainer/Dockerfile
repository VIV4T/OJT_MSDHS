FROM python:3.11-slim

# Keep Python predictable in containers
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app

# Install only Jupyter (and keep image small)
RUN pip install --no-cache-dir --upgrade pip \
 && pip install --no-cache-dir jupyter

# Jupyter uses 8888 by default
EXPOSE 8888

# Bind on all interfaces so the host can access it
CMD ["jupyter", "notebook",
     "--ip=0.0.0.0",
     "--port=8888",
     "--no-browser",
     "--allow-root",
     "--NotebookApp.token=",
     "--NotebookApp.password="]