## Jupyter/Zeppelin notebook conversion

#### _Note_ 
This library was out-of-date and has been updated to work with python 3.6 libraries.
This version does not support custom output paths, but will just output to the same folder as original, but with `.ipynb` extension.

Forked from `rdblue` and slightly modified.

---

This repo has code for converting Zeppelin notebooks to Jupyter's ipynb format.


## Use

To convert a notebook, run:

```
python jupyter-zeppelin.py note.json
```

This will create a file named using the Zeppelin note's name in the current directory.

### Supported conventions

This converter supports the following Zeppelin conventions:

* Code paragraphs are converted to code cells
* `%md` paragraphs are converted to Jupyter markdown cells
* `%html` paragraphs are converted to Jupyter code cells using cell magic `%%html`
* `%sql` paragraphs are converted to Jupyter code cells using cell magic `%%sql`
* Paragraphs with unknown magics are converted to raw cells
* TEXT output is converted to `text/plain` output
* HTML output is converted to `text/html` output; some style and JS may not work in Jupyter
* TABLE output is converted to simple `text/html` tables
  * `%html` table cells are embedded in the table HTML
  * Normal table cells are escaped and then embedded in the table HTML

### Mass conversions

To convert all `.json` in all subdirs recursively, locate to the root dir in question and use:

`find -name '*.json' -exec sh -c 'python3 <path-to-jupyter-zeppelin.py> "$0"' {} \;`