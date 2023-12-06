# The Pybot documentation

The pybot documentation use mkdocs https://www.mkdocs.org/ and the material theme https://squidfunk.github.io/mkdocs-material/.

## Install mkdocs

```
python -m venv venv
source venv/bin/activate
pip install mkdocs mkdocs-material
mkdocs --help
```

## Run the server

```
cd src
mkdocs serve
```

## Build and set the site folder as the new site version

```
rm -rf docs
cd src
mkdocs build
mv site ../docs
cd ..
rm docs/assets/images/favicon.png
cp favicon.png docs/assets/images
```

Then commit push to get the new version, the new site should be online.
