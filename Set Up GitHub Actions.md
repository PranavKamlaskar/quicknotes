## first setup git 
```
vim .gitignore
```
```
venv/
__pycache__/
*.pyc
*.pyo
*.pyd
*.db
.gitignore/
*.swp
.env
```

```
pip freeze > requirements.txt
```
```
git init
git add .
git remote add origin https://github.com/PranavKamlaskar/optimizer2.git
git branch -M main
git commit -m "first commit"
git push -u origin main
```




Create .github/workflows/test.yml:

```
name: Test-CI

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: CI is ready
        run: echo "DevOps setup complete"

```

Push the repo → pipeline triggers.
