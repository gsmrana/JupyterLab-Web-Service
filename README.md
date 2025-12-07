# JupyterLab Web Service
Deploy JupyterLab as web service to use it using any web browser.

## Install Python package manager UV
https://docs.astral.sh/uv/getting-started/installation

## Environment setup
1. Setup required packages.

```
uv sync
jupyter-lab --generate-config
jupyter-lab password
cat jupyter_lab_config.py >> ~/.jupyter/jupyter_lab_config.py
```

2. Install and run systemd service.

```
sudo cp jupyter_lab.service /etc/systemd/system/jupyter_lab.service
sudo systemctl daemon-reload
sudo systemctl enable jupyter_lab.service
sudo systemctl restart jupyter_lab.service
```

3. Browse url: http://localhost:8888/lab
