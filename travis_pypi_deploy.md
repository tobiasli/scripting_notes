My pypideploy routine:

1) Create proper package files: setup.py (with requires=[]) and .travis.yml
2) Build package locally and upload to pypi: `python setup.py sdist`
3) Upload package to pypi: `twine upload dist/*`         
4) Create pypi token for package: `https://pypi.org/manage/account/token/` 
5) Encrypt token using travis: `travis encrypt [token] --add deploy.password`

Note: May have to add the following to travis to aid in deploy:
deploy:
	skip_existing: true


6) Push to travis and check if build is successful.


Travis yaml example from dateparse-tobiasli:
.travis.yml

language: python
dist: xenial
sudo: false
python:
- '3.6'
- '3.7'
before_install:
- export PYTHONPATH=$PYTHONPATH:$(pwd)
install:
- pip install python-coveralls
- pip install pytest
- pip install pytest-cov
- pip install .
script:
- pytest --cov=dateparse dateparse
after_success:
- coveralls
deploy:
  provider: pypi
  user: __token__
  password:
    secure: [enter encrypted token]
  on:
    branch: master
  skip_existing: true
