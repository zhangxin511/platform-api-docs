Funding V2 API docs
===================

## Building locally
The docs are built using reStructured Text and
[Sphinx](http://www.sphinx-doc.org/en/stable/index.html). The 
[sphinxcontrib.httpdomain](https://pythonhosted.org/sphinxcontrib-httpdomain/) 
extension is used for describing RESTful HTTP APIs.

To get started, install [Python](https://www.python.org/) dependencies:
```
pip install -r requirements.txt
```

Then use make to build the html:

```
make html
```

This will output the html version of the docs to `_build/html`, just open the
`index.html` file to start browsing the docs. Run `make html` again to
regenerate the html after changes.

Changes will be published to [Read the Docs](https://www.readthedocs.org).
