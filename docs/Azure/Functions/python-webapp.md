---
title: Create WebApp with Python
---

- [Source Code](https://github.com/devignitelab/azure-functions/tree/main/python/PyWebApp)
- Create Virtual Environment in folder `antenv`
  ```bash
  python3.9 -m venv antenv
  ```
- Create Webapp
  - Using `up` command
    ```bash
    az webapp up --runtime PYTHON:3.9 --sku B1 --logs -g lab204 
    ```
    OR
  - Create Zip file for current directory
    ```bash
    zip -r main.zip . -x '.??*'
    ```
  - Create WebApp manually from portal named `nikx-app-01`
  - Deploy Zip file to webapp
    ```bash
    az webapp deploy -g lab204 --src-path main.zip -n nikx-app-01
    ```
- Configre WebApp settings `Custom startup command`
  ```bash
  python main.py
  ```


