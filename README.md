# git-coauthors

Lists all authors of a git repo as potential co-authors of a commit.

## Usage

    git coauthors

## Installation

Download the `git-coauthors` script to a directory in your `PATH`. I have `~/bin`
in my `PATH` and this is where I put it.

## Integration

These are some of the ways `git coauthors` can be integrated in a workflow.

### With `grep` and `pbcopy`

Quickly find a particular author and copy the _Co-Authored-By_ line to the
clipboard:

    git coauthors | grep Authorname | pbcopy

### With vim

#### Option 1: Using `read`

Paste the output of the above command directly in the buffer:

    :read !git coauthors | grep Authorname

#### Option 2: Using [vim-fzf][] to turn this into a completion:

This is my current workflow. I have an insert-mode keymap in my `.vimrc`:

    inoremap <expr> <c-x><c-g> fzf#vim#complete('git coauthors')

When I'm writing a commit message, I type the partial name of the co-author and
press <kbd>Ctrl-x</kbd><kbd>Ctrl-g</kbd> which pops up `fzf` with completions:

{screenshot}

Pressing <kbd>Enter</kbd> finishes the completion with the selected text.

### More

There are probably more ways to integrate this. If you come up with another
one, let me know!

[vim-fzf]: https://github.com/junegunn/fzf.vim
