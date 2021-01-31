# Cheatsheet

## bash

* `^old^new`

  ```bash
  $ git lgo
  $ ^lgo^log # runs `git log`
  ```

* previous command tokens

  ```bash
  !^      first arg
  !$      last arg
  !*      all args
  !:2     second arg
  !:2-3   range of args
  !:0     command
  !!      whole line
  ```

## git

* handy aliases

  ```bash
  alias gwip="git add . && git commit -am wip"
  alias gcan!="git commit --amend --no-edit"
  ```

* rebase workflow

  * `$ git rebase -i HEAD~(number of commits to rebase)`
    * `f` - combine with previous commit and discard message (good for `wip` commits)
    * `e` - good for breaking up a commit into smaller commits
      * `git reset`
      * create commits as necessary

## tmux

* copy/paste

  ```bash
  C-a [ # enter visual mode
  <space> # begin selection; can use vim motions
  <enter> # copy selection
  C-a ] # paste
  ```
