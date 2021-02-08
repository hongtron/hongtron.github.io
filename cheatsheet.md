Things I use (or want to use more often).

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

* template: simple script with args

  ```bash
  #!/bin/bash

  set -eu -o pipefail

  usage() {
    cat <<EOF
  $(basename "$0") [-f <value>]
  Options
    -f, --foo     First option
  EOF
  }

  while [[ $# > 0 && $1 == -* ]]; do
    case $1 in
      -f|--foo)
        shift
        export FOO=$1
        ;;
      -h|--help)
        usage
        exit
        ;;
    esac

    shift
  done
  ```

## git

* handy aliases

  ```bash
  alias gwip="git add . && git commit -m wip"
  alias gcan!="git commit --amend --no-edit"
  ```

* rebase workflow

  * `$ git rebase -i HEAD~(number of commits to rebase)`
    * `f` - combine with previous commit and discard message (good for `wip` commits)
    * `e` - good for breaking up a commit into smaller commits
      * `git reset HEAD~1`
      * create commits as necessary

## tmux

* copy/paste

  ```bash
  C-a [ # enter visual mode
  <space> # begin selection; can use vim motions
  <enter> # copy selection
  C-a ] # paste
  ```

## vim

* substitution with backreference

  ```
  :%s/\(SOME_PATTERN\)/\0/g # \0 is text matched by entire pattern
  :%s/\(FIRST_PATTERN\)\(SECOND_PATTERN\)/\1\2/g # \1 is first backref, \2 is second backref
  ```

* newlines
  * searching: `\n` is newline, `\r` is CR
  * replacing: `\r` is newline, `\n` is a null byte (0x00)
