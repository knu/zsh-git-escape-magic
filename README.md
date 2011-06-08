git-escape-magic for zsh
========================

Synopsis
--------

* git-escape-magic - zle tweak for git command line arguments

Description
-----------

This tweak eliminates the need for manually escaping shell (zsh)
meta-characters such as [~^{}] that are used for specifying a git
object (commit or tree).  Every time you type one of these characters
on a git command line, it is automatically escaped with a backslash as
necessary and as appropriate.

	% git reset HEAD
	                [Hit <^>]
	% git reset HEAD\^

How to set up
-------------

Put git-escape-magic somewhere in your $fpath and add these lines to
your .zshrc:

	autoload -Uz git-escape-magic
	git-escape-magic

If you are enabling url-quote-magic, make sure to load url-quote-magic
first and then load git-escape-magic.

License
-------

	Copyright (c) 2011 Akinori MUSHA

	Licensed under the 2-clause BSD license.
	See LICENSE for details.
