# Redline All-Sky Imager Raw PGM Data Readfile (REGO)

[![Github Actions - Tests](https://github.com/ucalgary-aurora/rego-imager-readfile/workflows/tests/badge.svg)](https://github.com/ucalgary-aurora/rego-imager-readfile/actions?query=workflow%3Atests)
[![PyPI version](https://img.shields.io/pypi/v/rego-imager-readfile.svg)](https://pypi.python.org/pypi/rego-imager-readfile/)
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![PyPI Python versions](https://img.shields.io/pypi/pyversions/rego-imager-readfile.svg)](https://pypi.python.org/pypi/rego-imager-readfile/)

Python library for reading REGO All-Sky Imager (ASI) stream0 raw PGM-file data. The data can be found at https://data.phys.ucalgary.ca.

## Installation

The rego-imager-readfile library is available on PyPI:

```console
$ python3 -m pip install rego-imager-readfile
```

## Supported Python Versions

rego-imager-readfile officially supports Python 3.6+.

## Examples

Example Python notebooks can be found in the "examples" directory. Further, some examples can be found in the "Usage" section below.

## Usage

Import the library using `import rego_imager_readfile`

### Read a single file

```python
>>> import rego_imager_readfile
>>> filename = "path/to/data/2020/01/01/fsmi_rego-654/ut06/20200101_0600_fsmi_rego-654_6300.pgm.gz"
>>> img, meta, problematic_files = rego_imager_readfile.read(filename)
```

### Read multiple files

```python
>>> import rego_imager_readfile, glob
>>> file_list = glob.glob("path/to/files/2020/01/01/fsmi_rego-654/ut06/*6300.pgm*")
>>> img, meta, problematic_files = rego_imager_readfile.read(file_list)
```

### Read using multiple worker processes

```python
>>> import rego_imager_readfile, glob
>>> file_list = glob.glob("path/to/files/2020/01/01/fsmi_rego-654/ut06/*6300.pgm*")
>>> img, meta, problematic_files = rego_imager_readfile.read(file_list, workers=4)
```

## Development

Clone the repository and install dependencies using Poetry.

```console
$ git clone https://github.com/ucalgary-aurora/rego-imager-readfile.git
$ cd rego-imager-readfile/python
$ make install
```

## Testing

```console
$ make test
[ or do each test separately ]
$ make test-flake8
$ make test-pylint
$ make test-pytest
```
