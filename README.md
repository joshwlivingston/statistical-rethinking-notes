# Notes on Statistical Rethinking

This website contains my 
[notes and code](https://joshwlivingston.github.io/statistical-rethinking-notes/) as
I work through
[Richard McElreath's](https://github.com/rmcelreath) 2025 
[course](https://github.com/rmcelreath/stat_rethinking_2025) on his book
[*Statistical Rethinking*](https://xcelab.net/rm/). A course in Bayesian
statistics, *Rethinking* is code-heavy and meant to be read sequentially, not 
as a reference. McElreath offers his flipped instruction course locally, also
publishing the 
[lectures](https://www.youtube.com/watch?v=FdnMWdICdRs&list=PLDcUM9US4XdPz-KxHM4XHt7uUVGWWVSus) 
online.

## Organization
The repository is organized into separate quarto files, which are stitched
together in `_quarto.yml`.

- `book-notes/`: contains notes and exercises directly from the textbook
- `course-notes/`: contains notes from pre-recorded lectures and slides
- `homework/`: contains homework solutions

## Dependencies
The quarto notebooks use both R and Python in their code.

### Quarto
First, install [Quarto](https://quarto.org/).

### Python
Create a virtual environment, using
[uv](https://docs.astral.sh/uv/getting-started/installation/):

```
uv venv
```

Then, install dependencies from `requirements.txt`:

```
uv pip install -r requirements.txt
```

Note: `pymc` compiles code at runtime, utilizing the `g++` compiler it finds in
the PATH.

### R
This project uses R 4.5.2, which can be installed using
[`rig`](https://github.com/r-lib/rig?tab=readme-ov-file#%EF%B8%8F-installing-rig-):

```
rig add 4.5.2
```

Then, use [`rv`](https://a2-ai.github.io/rv-docs/intro/installation/) to install
the R dependencies:

```
rv sync
```

### Hunspell

You'll need to have [Hunspell](https://github.com/hunspell/hunspell) installed
for the [spellcheck](https://github.com/christopherkenny/spellcheck) quarto
extension to work.

Windows:
```pwsh
choco install hunspell.portable
```

Mac:
```
brew install hunspell
```

Linux:
```
sudo apt-get install hunspell
```

#### en_US dictionary

After installing Hunspell, you must install the `en_US` dictionary.

Windows/Mac:

1. Download the
[dictionary](https://github.com/wooorm/dictionaries/tree/main/dictionaries/en)
files (both files: `.dic` and `.aff`).
2. Place them in hunspell's dictionary SEARCH PATH.

- To add a new directory to the search path, add the directory to the `DICPATH`
environment variable.
- To view the search path, use `hunspell -D`:

Linux:
```
sudo apt-get install hunspell-en-us
```

## Build

After installing the necessary dependencies, build the project:
```
quarto preview
```
