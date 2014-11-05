git-escape-magic for zsh
========================

Synopsis
--------

* git-escape-magic - zle tweak for git command line arguments

Description
-----------

If you are a hard-core zsh user that takes `extended_glob` seriously
for granted, you must be annoyed with git's refspec (notation to point
a commit, tree, etc.) that goes like `HEAD^` or `blahblah~3` because
the signs like `[^~{}]` are globbing meta-characters for zsh that
require escaping to be passed through to the git command.

Here is what this tweak is about.  It eliminates the need for manually
escaping those meta-characters.  The zle function it provides is
context aware and recognizes the characteristics of each subcommand of
git.  Every time you type one of these meta-characters on a git
command line, it automatically escapes the meta-character with a
backslash as necessary and as appropriate.

Examples:

	% git reset HEAD [Hit <^>]
	% git reset HEAD\^


	# Escaping takes place only if necessary
	% git reset HEAD\ [Hit <^>]
	% git reset HEAD\^


	% git reset HEAD@ [Hit <{>]
	% git reset HEAD@\{


	% git checkout HEAD [Hit <~>]
	% git checkout HEAD\~


	# Only pathspec follows after a double hyphen
	% git checkout -- * [Hit <~>]
	% git checkout -- *~


	# The add subcommand takes no refspec
	% git add * [Hit <~>]
	% git add *~

How to set up
-------------

Put the file `git-escape-magic` somewhere in your `$fpath` and add
these lines to your `.zshrc`:

	autoload -Uz git-escape-magic
	git-escape-magic

If you are enabling `url-quote-magic`, make sure to load it first and
then load `git-escape-magic`.

License
-------

Copyright (c) 2011, 2012, 2014 Akinori MUSHA

Licensed under the 2-clause BSD license.
See `LICENSE` for details.
