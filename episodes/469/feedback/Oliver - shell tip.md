In the latest episode, Allan says that the biggest thing he misses from
tcsh when going to other shells is the up cursor searching based on what
is already on the command-line.

For zsh, try binding the up cursor to history-beginning-search-backward.

I think that works similarly to tcsh. Personally, I don't like
how it positions the cursor at the end of the line. There is also
an up-line-or-search widget but that only searches based on the
first word. This being zsh, it is possible to programme the key to
match any particular preference. In this case, Zsh comes with some
existing widgets written as shell functions including one named
up-line-or-beginning-search which is close to what I use. Enabling it
would be something like the following:

  autoload -U up-line-or-beginning-search
  zle -N up-line-or-beginning-search
  bindkey '^[[A' up-line-or-beginning-search
  zstyle ':zle:(up|down)-line-or-beginning-search' leave-cursor false

Allan's second comment was about sometimes only wanting history from the
local terminal but also sometimes finding the shared history useful.
There is a set-local-history widget that allows you to bind a key
to toggle between just local and imported lines. Rather than toggle
between, I bind Ctrl-P/Ctrl-N to go up and down in local history only:

  up-line-or-local-history() {
    zle set-local-history 1
    zle up-history
    zle set-local-history 0
  }
  zle -N up-line-or-local-history
  bindkey '^P' up-line-or-local-history

That mostly works for me in the cases when I know I want local history
and Ctrl-P/N were already familiar (they are tcsh and ksh defaults).

oh-my-zsh may have other plugins but I don't use it. Feel free to
contact me with zsh questions if any other things bother you. Or if
any of this is unclear.

Thanks for the great podcasts!

Oliver
