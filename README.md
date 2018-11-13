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
1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
⋅⋅1. Ordered sub-list
4. And another item.

⋅⋅⋅You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

⋅⋅⋅To have a line break without a paragraph, you will need to use two trailing spaces.⋅⋅
⋅⋅⋅Note that this line is separate, but within the same paragraph.⋅⋅
⋅⋅⋅(This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses
- cong
