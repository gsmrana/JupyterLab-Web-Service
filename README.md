# JupyterLab Web Service
Deploy JupyterLab as a web service to use it using any web browser.

## Environment Setup

Install Python and UV Package Manager

https://docs.astral.sh/uv/getting-started/installation

```
winget install --id Python.Python.3.12
winget install --id=astral-sh.uv  -e
```

Install packages in a virtual environment

```
uv sync
```

Upgrade all packages

```
uv lock --upgrade
uv sync
```

## Configure the application

Configure jupyter-lab

```
jupyter-lab --generate-config
jupyter-lab password
cat jupyter_lab_config.py >> ~/.jupyter/jupyter_lab_config.py
```

## Install and run systemd service (Linux)

```
sudo cp jupyter_lab.service /etc/systemd/system/jupyter_lab.service
sudo systemctl daemon-reload
sudo systemctl enable jupyter_lab.service
sudo systemctl restart jupyter_lab.service
```

- Browse url: http://localhost:8888/lab
