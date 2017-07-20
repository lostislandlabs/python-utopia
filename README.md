# Utopia framework

This package provides the basic framework for the Utopia suite. It provides mechanisms for declaring and loading plugins and working with citations. Whereas it can be useful on its own, it is expected to be used alongside other packages that provide tools and plugins for doing useful analysis. This package does not yet work on Python 3+.

## Getting Started

In most cases, you will want the following four packages installed.

  1. **pyutopia** (this package) provides the base mechanisms for defining and loading plugins, adding tools, and manipulating citations.
  1. [**pyutopia-tools**](https://github.com/lostislandlabs/python-utopia-tools) provides utilities to various common resources such as PubMed, Crossref, ArXiv, etc. It also provides access utilities for working with the various Utopia servers. These tools can be used to create bespoke applications.
  1. [**pyutopia-plugins-common**](https://github.com/lostislandlabs/python-utopia-plugins-common) holds all the standard plugins used by the resolution pipeline.
  1. [**kend**](https://github.com/lostislandlabs/kend) provides utilities for accessing a kend server, and for parsing and serialising its data formats.

### Prerequisites

One of the dependencies of the Utopia packages is the [LXML](http://lxml.de/) package, which itself needs to be partly compiled from source that depends on the libxml2 and libxslt2 development libraries. Ensure these are present before continuing.

### Installing

You can either clone these repositories and build them yourself, or you can install the latest stable versions of the packages directly from PyPi:

```
$ pip install pyutopia-plugins-common # will pull in everything needed
```

## Usage

Utopia can be thought of as being in three separate parts: the _framework_, the _tools_, and the _plugins_. The framework is the low-level environment into which the tools and plugins fit, allowing them to extend the core functionality of Utopia via namespace packages and plugin resolution.

### Using Utopia's tools

The [**pyutopia-tools**](https://github.com/lostislandlabs/python-utopia-tools) package provides a set of Python modules for interacting with common services available in the bioinformatics and life sciences spaces. They can be found within the `utopia.tools` package.

#### Using `utopia.tools.arxiv`

```python
>>> import utopia.tools.arxiv as arxiv
>>> id = '1707.06154'
>>> arxiv.url(id)
'http://arxiv.org/abs/1707.06154'
>>> xml = arxiv.fetchXML(id) # Returns the ATOM item XML for that ID
>>> citation = arxiv.parseXML(xml) # Returns a citation dictionary
>>> citation = arxiv.resolve(id) # Wraps up the previous three steps
```

## License

This project is licensed under the GPLv3 License - see the [LICENSE.md](LICENSE.md) file for details
