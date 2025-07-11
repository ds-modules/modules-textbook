# The Data Science Modules Textbook

Authors: Alex Nakagawa, Chris Pyles

* Developed using [Jupyter Book](https://jupyter.org/jupyter-book/intro.html). Anything that you can't find in this README can be referenced in the docs.

## Documentation

Detailed build instructions can be found in [`build.md`](build.md)

The basic file structure for this repository is as follows:

```
├── _bibliography
├── _build
├── _data
├── _includes
├── _layouts
├── _sass
├── _site
├── assets
├── content
└── scripts
```

You will make all of your changes directly in the `content` directory. The content directory contains all of the Markdown (`.md`) and Jupyter Notebooks (`.ipynb`), which are later built and converted into html and css files.

### Create New Pages
* Create any changes you'd like to make within new Markdown (`.md`) files
* In order for your page to show up in the table of contents bar, you will also have to edit the sidebar file as well
  * `_data/toc.yml`


### Pasting Over Existing Notebooks

### Building the Site and Pushing Changes to Github Pages
When you are finished editing all changes in `content`, we do the following to build all of the necessary files and push to Github.

```
cd ..
jupyter-book build modules-textbook

cd modules-textbook
git add [CHANGED DIRECTORIES/FILES]
git commit -m '[ANY MESSAGE YOU'D LIKE]'
git push origin master
```
