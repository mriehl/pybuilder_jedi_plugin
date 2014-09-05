# PyBuilder jedi plugin

Lints your sources with the [jedi](https://jedi.jedidjah.ch/).

## Simple example
```bash
(example) mriehl@machine example $ cat src/main/python/mylib/__init__.py
def foobar():
    return 1 + "1"
(example) mriehl@machine example $ pyb analyze                          
PyBuilder version 0.10.33
Build started at 2014-09-05 09:25:38
------------------------------------------------------------
[WARN]  The jedi plugin is unstable since the linter API will probably change.
[INFO]  Building example version 1.0-SNAPSHOT
[INFO]  Executing build in /data/home/mriehl/example
[INFO]  Going to execute task analyze
[INFO]  Executing flake8 on project sources.  # <= flake8 does not find anything!
[INFO]  Executing jedi linter on project sources.
[WARN]  Jedi linter found 1 errors.
[WARN]  /data/home/mriehl/example/src/main/python/mylib/__init__.py:2:13: E11 TypeError: unsupported operand type(s) for +: <CompiledObject: 1> and <CompiledObject: '1'>
------------------------------------------------------------
BUILD FAILED - Jedi linter found errors
------------------------------------------------------------
Build finished at 2014-09-05 09:25:38
Build took 0 seconds (398 ms)
1 (example) mriehl@machine example $          
```

## Usage

Add plugin dependency to your build.py:
```python
use_plugin('pypi:pybuilder_jedi_plugin')
```

Run the linter:
```bash
pyb analyze
```

## Configuration

```python
project.set_property_if_unset("jedi_linter_break_build", False)
# Output every warning, not just the amount of warnings
project.set_property_if_unset("jedi_linter_verbose", False)
```

## Warning
The jedi linting capabilities are in a pre-alpha state, so it might crash or complain about things that are not actually problems.

Relevant: [Identifying Bugs Before Runtime With Jedi](https://www.youtube.com/watch?v=DfVHSw0iOsk)

## License
Apache license 2.0
