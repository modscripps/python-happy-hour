# conda environments
Conda is a (somewhat generic) package manager that is used quite widely in the Python community.

miniconda is a barebones version that provides the `conda` command line tool.

## miniconda installation
https://docs.conda.io/en/latest/miniconda.html

## conda defaults
`condarc-example` contains an example for some default settings, including default packages to be installed into every environment. They can be ignored by adding the `--no-default-packages` option when creating the environment.

## environment files
https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#create-env-file-manually

```yml
name: simple_env    # environment name
channels:
  - conda-forge     # community-driven channel for packages
dependencies:
  - python=3.10     # can provide specific version number
  - matplotlib      # for any package
  - numpy
  - scipy
  - pip
  # list packages to be installed via pip:
  - pip:
    - mixsea
    # install a local package in developer mode
    - "-e /Users/gunnar/Projects/python/gvpy"
```

Create the environment:
`conda env create -f environment.yml`

Then activate it:
`conda activate simple_env`

Install more packages from the command line into the activated environment:
`conda install <package-name>`

If you mess up an environment simply remove it
`conda env remove -n simple_env`
and re-install.

## freeze an environment
Export all installed packages and their version numbers with `conda env export > frozen_env.yml`. Unfortunately, this creates a list of *all* installed packages, not only the ones requested. Adding the option `--from-history` only lists requested packages (either installed from an environment file, the default packages list, or the command line) but no version numbers.

## speed things up
`conda install mamba` and call `mamba` instead of `conda`.

There is also `micromamba` as a full conda replacement but I have not tried it yet.

## alternatives to conda environments
[pipenv](https://pipenv.pypa.io/en/latest/) ?

## auto-activate conda environments
https://janosh.dev/blog/conda-auto-env
