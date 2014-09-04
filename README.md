# PyBuilder jedi plugin

Lints your sources with the [jedi](https://jedi.jedidjah.ch/).

## Usage

Add plugin dependency to your build.py:
```python
use_plugin('pypi:pybuilder_jedi_plugin')
```

Run the linter:
```bash
pyb verify
```

## Warning
The jedi linting capabilities are in a pre-alpha state, so it might crash or complain about things that are not actually problems.

Relevant: [Identifying Bugs Before Runtime With Jedi](https://www.youtube.com/watch?v=DfVHSw0iOsk)

## License
Apache license 2.0
