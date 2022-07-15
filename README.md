# JupyterLab Completer

## TL;DR

To get started:

```bash
# create a new environment
conda env create

# activate the environment
conda activate jupyterlab-completer

# install the extension in editable mode
python -m pip install -e .

# install your development version of the extension with JupyterLab
jupyter labextension develop . --overwrite

# build the TypeScript source after making changes
jlpm run build

# start JupyterLab
jupyter lab
```

The extension currently target **JupyterLab 3.1 or later**.

## Prerequisites

Writing an extension requires basic knowledge of JavaScript, Typescript and potentially Python.

_Don't be scared of Typescript, even if you never coded in TypeScript before you touch
JupyterLab you may find it easier to understand than pure JavaScript if you have a
basic understanding of object oriented programming and types._

You can create a [conda](https://docs.conda.io/en/latest/miniconda.html) environment to get started
after cloning this repository.

```bash
conda env create && \
  conda activate jupyterlab-completer
```

## Develop and Use the Extension

```bash
pip install -e .
jupyter labextension develop . --overwrite
```

Rebuild the extension:

```bash
jlpm run build
```

You can now start JupyterLab and check if your extension is working fine:

```bash
jupyter lab
```

### Change the Sources

If you want to develop and iterate on the code, you will need to open 2 terminals.

In terminal 1, go to the extension folder and run the following:

```bash
jlpm watch
```

Then in terminal 2, start JupyterLab with the watch flag:

```bash
jupyter lab --watch
```

From there, you can change your extension source code, it will be recompiled,
and you can refresh your browser to see your changes.

We are using [embedme](https://github.com/zakhenry/embedme) to embed code snippets into the markdown READMEs. If you make changes to the source code, ensure you update the README and run `jlpm embedme` from the root of the repository to regenerate the READMEs.

## Test the Extension

The extension are automatically tested for:

- Homogeneous configuration:  
  Configuration files are compared to the reference ones
- TypeScript code lint
- Installation in JupyterLab:  
  The installation is checked by listing the installed extension and running JupyterLab with the helper `python -m jupyterlab.browser_check`
- Integration test:  
  Those tests are emulating user action in JupyterLab to check the extension is behaving as expected.  
  The tests are defined in the `ui-tests` subfolder within the extension.
  This is possible thanks to a tool called [playwright](https://playwright.dev/).

## Install a Published Extension

Once your extension is published on [pypi.org](https://pypi.org/) (outside of this scope), you can install it
with the following command:

```bash
pip install <published_extension>
```
