# mkdocs repo for jorisdevrede.github.io

Source repository for jorisdevrede.github.io.

```bash
# install Linux
pip install mkdocs mkdocs-material

# deploy Linux
cd ../jorisdevrede.github.io
mkdocs gh-deploy -f ../mkdocs-jorisdevrede.github.io/mkdocs.yml --remote-branch master
```

```powershell
# install Windows
python -m venv venv
venv/Scripts/Activate.ps1
pip install mkdocs mkdocs-material

# deploy Windows
venv/Scripts/Activate.ps1
cd ../jorisdevrede.github.io
mkdocs gh-deploy -f ../mkdocs-jorisdevrede.github.io/mkdocs.yml --remote-branch master
```
