<!-- markdownlint-disable MD033 MD041 -->
<h1 align="center">
    docsai
</h1>

<p align="center">
    <strong>Generate markdown API documentation for Google-style Python docstring.</strong>
</p>

<p align="center">
    <a href="https://pypi.org/project/docsai/" title="PyPi Version"><img src="https://img.shields.io/pypi/v/docsai?color=green&style=flat"></a>
    <a href="https://pypi.org/project/docsai/" title="Python Version"><img src="https://img.shields.io/badge/Python-3.6%2B-blue&style=flat"></a>
    <a href="https://www.codacy.com/gh/khulnasoft/docsai/dashboard" title="Codacy Analysis"><img src="https://app.codacy.com/project/badge/Grade/1c8ad486ce9547b6b713cce7ca1d1ec3"></a>
    <a href="https://github.com/khulnasoft/docsai/actions?query=workflow%3Abuild-pipeline" title="Build status"><img src="https://img.shields.io/github/workflow/status/khulnasoft/docsai/build-pipeline?style=flat"></a>
    <a href="https://github.com/khulnasoft/docsai/blob/main/LICENSE" title="Project License"><img src="https://img.shields.io/badge/License-MIT-green.svg?style=flat"></a>
    <a href="https://gitter.im/khulnasoft/docsai" title="Chat on Gitter"><img src="https://badges.gitter.im/khulnasoft/docsai.svg"></a>
    <a href="https://twitter.com/khulnasoft" title="KhulnaSoft on Twitter"><img src="https://img.shields.io/twitter/follow/khulnasoft.svg?label=follow&style=social"></a>
</p>

<p align="center">
  <a href="#getting-started">Getting Started</a> •
  <a href="#features">Features</a> •
  <a href="#documentation">Documentation</a> •
  <a href="#support--feedback">Support</a> •
  <a href="#contribution">Contribution</a> •
  <a href="https://github.com/khulnasoft/docsai/releases">Changelog</a>
</p>

DocsAI makes it easy to generate beautiful markdown documentation for your Python API (see this [example](./docs)). It provides a [simple command-line interface](#cli-interface) as well as a [Python API](#programmatic-api) to get full-fledged API documentation within seconds based on all of the [Google-style docstrings](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html) in your code. This markdown documentation can be pushed to Github or integrated into your MkDocs site.

## Highlights

- ⏱&nbsp; Simple CLI to generate markdown docs in seconds.
- 📋&nbsp; Supports [Google-style Python Docstrings](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html).
- 📚&nbsp; Compatible with Github Markdown and MkDocs.

## Getting Started

### Installation

> _Requirements: Python 3.6+._

```bash
pip install docsai
```

### Usage

To generate Markdown-based API documentation for your Python project, simply execute:

```bash
docsai path/to/your/package
```

The path can be either a python package (folder) or a specific script. You can also specify one or multiple module-, class- or function-imports:

```bash
docsai my_package.AwesomeClass
```

With the default configuration, the Markdown documentation will be generated inside the `./docs` folder in your working directory. You can find additional configuration options in the [documentation section](#cli-interface).

| Type                     | Channel                                              |
| ------------------------ | ------------------------------------------------------ |
| 🚨&nbsp; **Bug Reports**       | <a href="https://github.com/khulnasoft/docsai/issues?utf8=%E2%9C%93&q=is%3Aopen+is%3Aissue+label%3Abug+sort%3Areactions-%2B1-desc+" title="Open Bug Report"><img src="https://img.shields.io/github/issues/khulnasoft/docsai/bug.svg?label=bug"></a>                                 |
| 🎁&nbsp; **Feature Requests**  | <a href="https://github.com/khulnasoft/docsai/issues?q=is%3Aopen+is%3Aissue+label%3Afeature+sort%3Areactions-%2B1-desc" title="Open Feature Request"><img src="https://img.shields.io/github/issues/khulnasoft/docsai/feature.svg?label=feature%20request"></a>                                 |
| 👩‍💻&nbsp; **Usage Questions**   |   <a href="https://stackoverflow.com/questions/tagged/khulnasoft" title="Open Question on Stackoverflow"><img src="https://img.shields.io/badge/stackoverflow-khulnasoft-orange.svg"></a> <a href="https://gitter.im/khulnasoft/docsai" title="Chat on Gitter"><img src="https://badges.gitter.im/khulnasoft/docsai.svg"></a> |
| 🗯&nbsp; **General Discussion** | <a href="https://gitter.im/khulnasoft/docsai" title="Chat on Gitter"><img src="https://badges.gitter.im/khulnasoft/docsai.svg"></a> <a href="https://twitter.com/khulnasoft" title="KhulnaSoft on Twitter"><img src="https://img.shields.io/twitter/follow/khulnasoft.svg?style=social"></a>|
| ❓&nbsp; **Other Requests** | <a href="mailto:info@khulnasoft.com" title="Email KhulnaSoft DevOps"><img src="https://img.shields.io/badge/email-KhulnaSoft-green?logo=mail.ru&logoColor=white"></a> |

## Features

<p align="center">
  <a href="#source-code-linking">Source Code Linking</a> •
  <a href="#api-overview">API Overview</a> •
  <a href="#mkdocs-integration">MKDocs Integration</a> •
  <a href="#docstyle-validation">Docstyle Validation</a> •
  <a href="#print-to-console">Print to Console</a>
</p>

### Source Code Linking

DocsAI is capable to insert a badge on the right side of every module, class, method or function with a link the correct source-code file and line number. The default configuration will create relative paths to navigate within the Github Repo. This is useful if the documentation is hosted within the same repository as the source-code. If, the documentation is hosted outside of the Github repository, it is recommended to set the `src-base-url`:

```bash
docsai --src-base-url="https://github.com/example/my-project/blob/main/" my_package
```

The `src-base-url` is used as a prefix for all source-code linkings in the documentation.

### API Overview

An API overview might be very useful in case your project has a large number modules, classes and functions. You can specify an `overview-file` with the docsai command to activate the generation of an API overview:

```bash
docsai --overview-file="README.md" my_package
```

The API overview will be written as markdown to the specified file with separated lists for all modules, classes, and functions of your project:

### MkDocs Integration

The markdown documentation generated by docsai can be easily integrated into your [mkdocs](https://www.mkdocs.org/) documentation site:

1. Generate the markdown documentation into a subfolder (e.g. `api-docs`) inside your mkdocs documentation. We recommend to use the `overview-file` option and set the source-code URL via `src-base-url`, otherwise the source-code linking would not work:

```bash
docsai \
    --output-path="./docs/api-docs" \
    --overview-file="README.md" \
    --src-base-url="https://github.com/example/my-project/blob/main/" \
    my_package
```

2. Install and apply the [awesome-pages mkdocs plugin](https://github.com/lukasgeiter/mkdocs-awesome-pages-plugin). This enables mkdocs to automatically discover and include all markdown files. The alternative would be to manually include all generated markdown files in the navigation section of the `mkdocs.yaml`. In order to use the awesome-pages plugin you need to 1) install the plugin via pip 2) Include it in the plugin section `mkdocs.yaml` and remove the navigation section (needs to be handled with `.pages` files).

3. If you used the `overview-file` option, a `.pages` file will be automatically created. You can also manually create the `.pages` file within the api-docs subfolder (e.g. `api-docs`) with the following content:

    ```yaml
    title: API Reference
    nav:
       - Overview: README.md
       - ...
    ```

Once you run or deploy your mkdocs documentation, you will see the API Reference section with all of your API markdown documentation.

### Docstyle Validation

DocsAI can only parse valid Google-style docstring. To prevent the generation of invalid markdown documentation, you can use the `validate` flag:

```bash
docsai --validate my_package
```

This will run [pydocstyle](https://github.com/PyCQA/pydocstyle) on your docstring and cancel the generation if an issue is found.

### Print to Console

To get the markdown documentation as console output instead of the file generation, specify `stdout` as the `output-path`:

```bash
docsai --output-path=stdout my_package
```

## Documentation

### CLI Interface

<!-- generated via typer-cli: typer src/docsai/_cli.py utils docs -->

```bash
docsai [OPTIONS] PATHS...
```

**Arguments**:

* `PATHS...`: Selected paths or imports for markdown generation.  [required]

**Options**:

* `--output-path TEXT`: The output path for the creation of the markdown files. Set this to `stdout` to print all markdown to stdout.  [default: ./docs/]
* `--src-base-url TEXT`: The base repo link used as prefix for all source links. Should also include the branch name.
* `--overview-file TEXT`: Filename of overview file. If not provided, no API overview file will be generated.
* `--remove-package-prefix / --no-remove-package-prefix`: If `True`, the package prefix will be removed from all functions and methods.  [default: True]
* `--ignored-modules TEXT`: A list of modules that should be ignored.  [default: ]
* `--watermark / --no-watermark`: If `True`, add a watermark with a timestamp to bottom of the markdown files.  [default: True]
* `--validate / --no-validate`: If `True`, validate the docstrings via pydocstyle. Requires pydocstyle to be installed.  [default: False]
* `--install-completion`: Install completion for the current shell.
* `--show-completion`: Show completion for the current shell, to copy it or customize the installation.
* `--help`: Show this message and exit.

### Programmatic API

DocsAI can also be used and integrated via its [Python API](https://github.com/khulnasoft/docsai/tree/main/docs). For example, to generate markdown for an arbitrary Python import or object:

```python
from docsai import MarkdownGenerator

generator = MarkdownGenerator()

# Select a module (e.g. my_module) to generate markdown documentation
markdown_docs = generator.import2md(my_module)
```

To programmatically generate all markdown documentation files you can use [`generate_docs`](https://github.com/khulnasoft/docsai/blob/main/docs/docsai.generator.md#function-generate_docs):

```python
from docsai import generate_docs

# The parameters of this function correspond to the CLI options
generate_docs(["my_module"], output_path="./docs")
```

The full Python API documentation can be found [here](https://github.com/khulnasoft/docsai/tree/main/docs) _(generated via docsai)_.

## Contribution

- Pull requests are encouraged and always welcome. Read our [contribution guidelines](https://github.com/khulnasoft/docsai/tree/main/CONTRIBUTING.md) and check out [help-wanted](https://github.com/khulnasoft/docsai/issues?utf8=%E2%9C%93&q=is%3Aopen+is%3Aissue+label%3A"help+wanted"+sort%3Areactions-%2B1-desc+) issues.
- Submit Github issues for any [feature request and enhancement](https://github.com/khulnasoft/docsai/issues/new?assignees=&labels=feature&template=02_feature-request.md&title=), [bugs](https://github.com/khulnasoft/docsai/issues/new?assignees=&labels=bug&template=01_bug-report.md&title=), or [documentation](https://github.com/khulnasoft/docsai/issues/new?assignees=&labels=documentation&template=03_documentation.md&title=) problems.
- By participating in this project, you agree to abide by its [Code of Conduct](https://github.com/khulnasoft/docsai/blob/main/.github/CODE_OF_CONDUCT.md).
- The [development section](#development) below contains information on how to build and test the project after you have implemented some changes.

## Development

> _**Requirements**: [Docker](https://docs.docker.com/get-docker/) and [Act](https://github.com/nektos/act#installation) are required to be installed on your machine to execute the build process._

To simplify the process of building this project from scratch, we provide build-scripts - based on [ml-buildkit](https://github.com/khulnasoft/ml-buildkit) - that run all necessary steps (build, check, test, and release) within a containerized environment. To build and test your changes, execute the following command in the project root folder:

```bash
act -b -j build
```

Refer to our [contribution guides](https://github.com/khulnasoft/docsai/blob/main/CONTRIBUTING.md#development-instructions) for more detailed information on our build scripts and development process.

---

Licensed **MIT**. Created and maintained with ❤️&nbsp; by developers from KhulnaSoft.
