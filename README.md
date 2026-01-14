# Notes on Statistical Rethinking

This repo contains my 
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
The repoistory is organized into separate quarto files, which are stitched
together in `_quarto.yml`.

- `book-notes/`: contains notes and exercises directly from the textbook
- `course-notes/`: contains notes from pre-recorded lecutres and slides
- `homework/`: contains homework solutions

## Setup

### python
While the original code in the book uses the custom R `rethinking` package, I
have implemented the code examples and homework solutions using `pymc5`.

First, create a virtual environment, using
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

### quarto
In addition to [Quarto](https://quarto.org/), you must install the following
system depdencies:

#### Hunspell

[Hunspell](https://github.com/hunspell/hunspell) is *the* open source
spellchecking library. It is used by the
[spellcheck](https://github.com/christopherkenny/spellcheck) quarto extension.

**Windows**:
```pwsh
choco install hunspell.portable
```

**Mac**:
```
brew install hunspell
```

**Linux**:
```
sudo apt-get install hunspell
```

#### en_US dictionary

After installing Hunspell, you must install the `en_US` dictionary.

**Windows**/**Mac**:
Download the
[dictionary](https://github.com/wooorm/dictionaries/tree/main/dictionaries/en)
files (both files: `.dic` and `.aff`), and place them in hunspell's dictionary
SEARCH PATH.

To view the search path, use the command line:
```
hunspell -D
```

To add a new directory to the search path, add the directory to the `DICPATH`
environment variable.

**Linux**:
```
sudo apt-get install hunspell-en-us
```

## Build

After installing the necessary dependencies, build the project:
```
quarto preview
```

## Attribution

This repository contains my work and solutions for the course
[Statistical Rethinking (2025 Edition)](https://github.com/rmcelreath/stat_rethinking_2025), 
which is licensed under CC0 1.0 Universal.

Code examples are adapted from Richard McElreath’s original course materials
and/or [*Statistical Rethinking*](https://xcelab.net/rm/).
