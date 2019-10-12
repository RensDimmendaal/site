---
title: "HOW TO: Automate creation of conda environments"
date: 2019-10-09T17:20:36+02:00
tags: howto, conda
draft: false
---

Do you:

* Always have to google how to create a new environment?
* Forget to activate the right environment?
* Forget the name of your conda  environments?

Then these aliases for your `.bashrc` or `.zshrc` file might help.

```
function mkconda() {
    dir=$(echo $PWD | rev | cut -d/ -f1 | rev)
    conda create -n $1 -y python=3.7
    conda deactivate
    conda activate $1
}
```

This gives you the option to run `mkconda` and it will create a new conda environment with the same name as the current directory.

If you add:

```bash
function ca() {
    dir=$(echo $PWD | rev | cut -d/ -f1 | rev)
    conda deactivate
    conda activate ${dir}
}
```

Then you can use `ca` from your project root to easily activate the relevant conda  environment.
As a bonus if you often forget to activate the right environment then you can use aliases:

```bash
# Python aliases
alias jn="ca && jupyter notebook"
alias jl="ca && jupyter lab"
alias ip="ca && ipython"
```