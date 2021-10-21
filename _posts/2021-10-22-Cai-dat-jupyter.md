---
title: Cài đặt Jupyter
date: 2021-10-22 05:08:00 AM
last_modified_at: 
tags: python
toc: false
---

```shell
pip install --user jupyterlab
```

Tạo file cấu hình Jupyter Lab

```shell
jupyter-lab --generate-config
```



Chỉnh sửa các giá trị của [file cấu hình](https://jupyter-notebook.readthedocs.io/en/stable/config.html){:target="_blank"}

```python
c.ServerApp.root_dir = "/default/directory"
# ...
# c.ServerApp.token = ''
```

Thêm các Kernel khác vào Jupyter Server bằng cách:

- Cài đặt [`ipykernel`](https://pypi.org/project/ipykernel/){:target="_blank"} trong môi trường muốn thêm vào Jupyter

- ```python
  python -m ipykernel install --user --name myenv --display-name "Python (myenv)"
  ```



---

References:

[https://jupyter.org/install](https://jupyter.org/install){:target="_blank"}

[https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments){:target="_blank"}