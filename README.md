# py-package-logging

## Install
```bash
pip install py-pkg-logging
```

## Use
### Package-level logging
Set up package-level logging in `pkg/__init__.py`
```python
# -- set up logging: ----------------------------------------------------------
import logging as _logging
import py_pkg_logging as _ppl

name = "pkg" # define this on a per-package basis

_log_config = _ppl.LogConfig(name = name, log_file=f"{name}.log")

_logger = _logging.getLogger(f'{name}.{__name__}')
_logger.info(f"Logs for {name} will be saved to: {_log_config.log_fpath}")
_logger.debug(f"Importing from local install location: {__file__}")

# the rest of your package-level import statements

```

### Example use of in-line function-call logging:
```python

# -- set up logger: -----------------------------------------------------------
import py_pkg_logging
import logging

logger = logging.getLogger(__name__)


@py_pkg_logging.log_function_call(logger)
def persistent_executer(a, b, c):
    return (a + b) * c

```
