---
title: "HOW TO: Automate creation of conda environments"
date: 2019-10-8
tags: howto, conda
draft: false
---

Do you:
* Always have to google how to create a new environment?
* Forget to activate the right environment?
* Forget the name of your conda  environments?

Then these aliases for your `.bashrc` or `.zshrc` file might help.

```
function mkproj() {
    mkdir $1
    cd $1
    conda create -n $1 -y python=3.7
    conda deactivate
    conda activate $1
}
```

This gives you the option to run `mkproj projectname` and  it will make a new directory and conda environment of name `projectname`.

If you add:

```bash
function ca() {
    dir=$(echo $PWD | rev | cut -d/ -f1 | rev)
    conda deactivate
    conda activate ${dir}
}
```

Then you can easily activate the relevant conda  environment if you are in the  project's home directory.
Finally if you often forget to activate the conda environment before going into jupyter lab then these aliases might help:

```bash
# Python aliases
alias jn="ca  && jupyter notebook"
alias jl="ca && jupyter lab"
alias ip="ca && ipython"
```