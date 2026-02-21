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
uv run jupyter-lab --generate-config
uv run jupyter-lab password
cat jupyter_lab_config.py >> ~/.jupyter/jupyter_lab_config.py
```

## Run the application

```
uv run jupyter-lab --notebook-dir=Notebooks
```

- Browse: http://localhost:8888/lab

## Install and run systemd service (Linux)

```
sudo cp jupyter_lab.service /etc/systemd/system/jupyter_lab.service
sudo systemctl daemon-reload
sudo systemctl enable jupyter_lab.service
sudo systemctl restart jupyter_lab.service
```

## Install and run launchd service (macOS)

```
sudo cp com.jupyterlabweb.service.plist /Library/LaunchDaemons/
sudo chown root:wheel /Library/LaunchDaemons/com.jupyterlabweb.service.plist
sudo chmod 644 /Library/LaunchDaemons/com.jupyterlabweb.service.plist
```

```
# first start
sudo launchctl load -w /Library/LaunchDaemons/com.jupyterlabweb.service.plist

# restart
sudo launchctl kickstart -k system/com.jupyterlabweb.service
```
