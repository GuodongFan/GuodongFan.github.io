---
title: Kubernetes
published: true
category: work
tag: Microservice
---

参考：https://github.com/eon01/kubernetes-workshop

## Environment

Ubuntu 18.04, python 3.6.

Install PIP

```
apt-get install python3-pip
```

Install Virtualenvwrapper, which is a virtual environment manager.

```
pip3 install virtualenvwrapper
```

Create a folder for your virtualenvs and set it as WORKON_HOME.

```
mkdir  ~/dev/PYTHON_ENVS
export WORKON_HOME=~/dev/PYTHON_ENVS
```

Inorder to source the environment details when the user login, add the following lines to ~/.bashrc

```
source "/usr/local/bin/virtualenvwrapper.sh"
export WORKON_HOME="~/dev/PYTHON_ENVS"
```

Create then activate the new environment.

```
mkvirtualenv --python=/usr/bin/python3 trendinggitrepositories
workon trendinggitrepositories
```

Create the application directories.

```
mkdir trendinggitrepositories
cd trendinggitrepositories
mkdir api
cd api
```

Install Flask.

```
pip install flask
```

## Developing a trending Git Repositories API (Flask)

```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
    return "Hello, World!"

if __name__ == '__main__':
    app.run(debug=True)
```