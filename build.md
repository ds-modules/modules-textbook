# Build Instructions for Modules Textbook

This file contains instructions for adding modules to this site. It is built on a [Jupyter Book distribution](https://jupyter.org/jupyter-book/intro.html) and hosted on Github Pages.

## Instructions for Adding Modules

This section details instructions on how to add a featured module.

1. Clone the module repo and locally. 
2. Copy the files from the module repo into the `content` directory of this repo. _Make a new folder for this module._ The folder name should be the name of the class. For example, if I were adding the ECON 101B module, I would add the files as below.

```
| modules-textbook
	| content
		| econ-101b
			| - nb1.ipynb
			| - nb2.ipynb
```

3. Make any edits necessary to the notebooks.
4. Create an [introduction page](#module-intro) for your module.
5. Add the module as a chapter to the `data/_toc.yml` file. Instructions on how to add this are [below](#adding-toc).
6. Build the book by navigating to the modules-textbook repo in your terminal and running the following:

```bash
jupyter-book build . --overwrite
```

7. (Optional) Run a [docker server](#docker) to look over your edits and make sure everything works OK. To run the docker server, run the command below in your terminal. Make sure that you set `/full/path/to/modules-textbook` to the full path to the repo.

```bash
docker run --rm --security-opt label:disable  \
   -v /full/path/to/your/book:/srv/jekyll \
   -p 4000:4000 \
   -it -u 1000:1000 \
   emdupre/jupyter-book bundle exec jekyll serve --host 0.0.0.0
```

8. Commit your changes and push to Github.

<div id="module-intro"></div>

## Module Intros

When you write the intro to your module, it should include three things: the course description, a description of the module, and the module developers. The introduction should be a Markdown file or a Jupyter Notebook with no code. 

A sample structure for the file is below.

```markdown
# Introduction to the Economics Modules

## ECON 101B: <!-- Course Title -->

**Course Description:** <!-- course description goes here -->

**Module Description:** <!-- module description goes here -->

**Developers:** <!-- list developers here -->
```


<div id="adding-toc"></div>

## Adding Chapters to `data/_toc.yml`

To add a chapter to the table of contents, start by intializing a chapter with the subject as the title. For example, if I were adding ECON 101B, the chapter would be titled "Economics". Place the chapter alphabetically in the list by the chapter name (so "Economics" would go after City Planning but before English). Set the URL for this page to your intro for the chapter. Make sure that the `not_numbered` and `expand_sections` attributes are set to `true`. Please also include a comment above the chapter indicating which subject the chapter is.

To add the notebooks for this module, add them as elements to the `sections` attribute for the chapter. Title each notebook appropriately and make sure that each section has the `not_numbered` attribute set to `true`. 

When you add file URLs, do not include the file extensions. When you build the notebook, Jupyter Book will automatically detect files with matching names and either a `.ipynb` or `.md` extension. Also, all URLs should be relative to the `content` directory, as this is where Jupyter Book looks for content files and how it structures the `_build` directory.

An example of a chapter added to the YAML file is below.

```yaml
# Economics Chapter
- title: Economics
  url: /econ-101b/intro
  not_numbered: true
  expand_sections: true
  sections:
  - title: Problem Set 1
  	url: /econ-101b/ps1
  	not_numbered: true
  - title: Problem Set 2
  	url: /econ-101b/ps2
  	not_numbered: true
  - title: Problem Set 3
  	url: /econ-101b/ps3
  	not_numbered: true
```

<div id="docker"></div>

## Docker Server

More information on how to set your computer up for the Docker server can be found on the [Jupyter Book website](https://jupyter.org/jupyter-book/guide/03_build.html#building-your-site-locally-with-containers-docker).