# Statistical Rethinking (2nd Edition)

This repo contains my notes and code as I work through 
[Richard McElreath's](https://github.com/rmcelreath) 2025 
[course](https://github.com/rmcelreath/stat_rethinking_2025) on his book
[*Statistical Rethinking*](https://xcelab.net/rm/). A course in Bayesian
statistics, *Rethinking* is code-heavy and meant to be read sequentially, not 
as a reference. McElreath offers his flipped instruction course locally, also
publishing the 
[lectures](https://www.youtube.com/watch?v=FdnMWdICdRs&list=PLDcUM9US4XdPz-KxHM4XHt7uUVGWWVSus) 
online.

## Organization
The repoistory is organized into separate quarto files,  which can each be 
locally rendered.

- `book/`: contains notes and exercises directly from the textbook
- `course/`: contains notes from pre-recorded lecutres and slides
- `homework/`: contains homework solutions

## Setup
The examples in the book require installation of the 
[{rethinking}](https://github.com/rmcelreath/rethinking) R package. Follow
these steps to install:

1. Download `{rstan}` from [mc-stan.org](https://mc-stan.org)
2. Download `{rethinking}`:
```r
# Experiemntal branch contains new tools for 2nd edition
devtools::install_github("rmcelreath/rethinking",ref="Experimental")
```
