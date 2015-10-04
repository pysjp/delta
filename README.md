# Delta

Delta is both a Go library and a command-line utility for text diffs.

## Installation

    go get github.com/octavore/delta/delta

If `$GOPATH/bin` is on your `$PATH`, run `delta -h` for usage.

## Description

Delta implements two diff functions: Smith-Waterman, and histogram diff.

[Smith-Waterman](https://en.wikipedia.org/wiki/Smith%E2%80%93Waterman_algorithm)
is a dynamic programming algorithm for aligning two sequences, in this case text
sequences. It originates from bioinformatics, where it is used for aligning DNA sequences.

[histogram diff](http://download.eclipse.org/jgit/docs/jgit-2.0.0.201206130900-r/apidocs/org/eclipse/jgit/diff/HistogramDiff.html)
is a diff algorithm first implemented in `JGit` and subsequently ported over
to `git`, where it can be used with the `git diff --histogram` command. This
implementation post processes the histogram diff in order to push down match
regions as far as possible. `git` also post processes diffs.

## Configure git

The `delta` binary must be on your `$PATH` in order for this work. The following are helpers for adding `delta` to your `~/.gitconfig` file.

    delta --install   # makes delta the default for `git difftool`
    delta --uninstall # remove delta from your gitconfig
