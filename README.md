# flask-app
Getting started with Flask

## Create Virtualenv and Activate
```
virtualenv env
source env/bin/activate
```

## Install Dependencies
```
pip install -r requirements.txt
```

## Run The Application
```
export FLASK_APP=app
export FLASK_ENV=development
flask init-db
flask run --host=0.0.0.0 --port=5000
```

## Make the Project Installable
```setup.py`` and ```MANIFEST.in``` describes how to install the project

## Install the Project (in editable or development mode)
```
pip install -e .
pip list
```

## Test Coverage
```pytest``` and ```coverage``` are listed in ```requirements.txt```

```setup.cfg``` file makes running tests less verbose

To run tests:
```
pytest
```

To measure and view coverage:
```
coverage run -m pytest
coverage report
coverage html
```

## Deploy to Production
Build distribution file using ```wheel```
```
pip install wheel
python setup.py bdist_wheel
```
The ```bdist_wheel``` command will build a wheel distribution file.

You can find the file in ```dist/app-0.0.1-py3-none-any.whl```. Copy this file to another machine, set up a new virtualenv, then install the file with ```pip```.
```
pip install app-0.0.1-py3-none-any.whl
```

Pip will install your project along with its dependencies.

Since this is a different machine, you need to run ```init-db``` again to create the database in the instance folder.
```
export FLASK_APP=app
flask init-db
```

## Configure the Secret Key
```
python -c 'import os; print(os.urandom(16))'

b'_5#y2L"F4Q8z\n\xec]/'
```

Create the ```config.py``` file in the instance folder, which the factory will read from if it exists. Copy the generated value into it.

venv/var/flaskr-instance/config.py
```
SECRET_KEY = b'_5#y2L"F4Q8z\n\xec]/'
```

## Run with Production Server
```
pip install waitress
waitress-serve --call 'app:create_app'

Serving on http://0.0.0.0:8080
```
