
# OpenAlea Documentation

[![Documentation Status](https://readthedocs.org/projects/sconsx/badge/?version=latest)](https://sconsx.readthedocs.io/en/latest/?badge=latest)

# Description

OpenAlea is an open source project primarily aimed at the plant research community. It is a distributed collaborative effort to develop Python libraries and tools that address the needs of current and future works in Plant Architecture modeling. OpenAlea includes modules to analyze, visualize, and model the functioning and growth of plant architecture.

## Institutes (Sponsors)

OpenAlea is developed, maintained and mainly funded by three institutes: CIRAD, INRIA, and INRAE.

## License

OpenAlea is licensed under the CeCILL-C free software license agreement.

## Official documentation

http://openalea.rtfd.io

# Installation

Installation procedure for OpenAlea is straightforward and can be done in a few steps. Please follow the installation instructions in the installation section.

# Usage

Tutorials to use the different features of OpenAlea can be found in the tutorials section.

# Troubleshooting

## Installation Issues

### Dependency Errors

Description Installation fails with dependency errors.

**Solution**: Ensure that you are using the latest version of Miniforge and that your environment is clean before installing OpenAlea. You can remove an existing environment with:

```bash
   mamba env remove -n openalea
```
Then, try creating the environment again.

### Command Not Found

**Description**: "mamba" command not found.

**Solution**: Make sure Miniforge is correctly installed and added to your system's PATH. You might need to restart your terminal or Miniforge Prompt.

## Module Import Issues

### Modules Not Found in Jupyter Notebook

**Description**: OpenAlea modules not found when importing in a Jupyter notebook.

**Solution**: Ensure that you have activated the OpenAlea environment before starting the Jupyter notebook. You can activate the environment with:

```bash
   mamba activate openalea
```

If the issue persists, try installing the Jupyter notebook within the OpenAlea environment:

```bash
   mamba install notebook
```

## Updating OpenAlea

### How to Update OpenAlea

To update OpenAlea and its dependencies, activate your OpenAlea environment and run:

```bash
   mamba update -c openalea3 openalea.plantgl openalea.lpy openalea.visualea openalea.mtg
```

## Contribution

### How to Contribute to OpenAlea
The main way to contribute is to fork the package repository you are interested in on [GitHub](https://github.com/openalea),
see the [How to](https://openalea.readthedocs.io/en/latest/development/contributing.html#how-to-contribute) in the Openalea documentation.


## Additional Resources

### Tutorials and Examples

More tutorials and examples can be found in the [official documentation](https://openalea.readthedocs.io/en/latest/tutorials/index.html)


# Contact

For further assistance, you can reach out to the development team creating an [issue on github](https://github.com/openalea/openalea/issues)
