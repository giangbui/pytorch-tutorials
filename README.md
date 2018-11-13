# sheepdog

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/0069fa67707f48a7aabfe9de6b857392)](https://www.codacy.com/app/uc-cdis/sheepdog?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=uc-cdis/sheepdog&amp;utm_campaign=Badge_Grade)
[![Codacy Badge](https://api.codacy.com/project/badge/Coverage/0069fa67707f48a7aabfe9de6b857392)](https://www.codacy.com/app/uc-cdis/sheepdog?utm_source=github.com&utm_medium=referral&utm_content=uc-cdis/sheepdog&utm_campaign=Badge_Coverage)

## Installation

### For General Usage

To install sheepdog for use with other Gen3 services, running these commands is sufficient.

```bash
python setup.py build
python setup.py install
```

### For Development

```bash
pip install -r dev-requirements.txt
python setup.py develop
```

(`dev-requirements.txt` contains requirements for testing and doc generation.
Installing with `python setup.py develop` avoids literally installing anything
but creates an egg link to the source code.)

## Minimal Usage Example

```python
import sheepdog
import datamodelutils
from dictionaryutils import dictionary
from gdcdictionary import gdcdictionary
from gdcdatamodel import models, validators

dictionary.init(gdcdictionary)
datamodelutils.validators.init(validators)
datamodelutils.models.init(models)
blueprint = sheepdog.create_blueprint(name='submission')

app = Flask(__name__)
app.register_blueprint(blueprint)
```

## Documentation

Auto-documentation is set up using
[Sphinx](http://www.sphinx-doc.org/en/stable/). To build it, run
```bash
cd docs
make html
```
which by default will output the `index.html` page to
`docs/build/html/index.html`.

## Test
3. Indexing void object for fully control the bucket structure.

Indexd supports void or blank records that allows users to pre-register data files in indexd before actually registering them. The complete flow contains three main steps: pre-register, hash/size/url populating and data node registration:\
    \t- Fence requests blank object from indexd. Indexd creates an object with no hash, size, and urls except the `uploader` field.\
    \t- Indexd listener mornitors bucket update, update to indexd with url, hash, size.\
    \t- The client application (windmill or gen3-data-client) lists records for data files which the user needs to submit to the graph. The user fills all empty fields and submit the request to indexd to update the `acl`
