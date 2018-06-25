git-pr
######

``git-pr`` is a set of git commands built to locally checkout and view/test 
Github Pull Requests.

Installation
============

Clone the repository and copy the contents of the ``bin/`` directory to 
``.local/bin`` or anywhere in your ``$PATH``.

``mkdir -p .local/bin; cp bin/* .local/bin/``

Commands
========

The tool contains the following commands

``pr-checkout <remote> <PR number> [<base>]``
-------------------------------------------

Checkout the PR number ``<PR number>`` from repository at ``<remote>``.
The ``<base>`` is the base branch that the PR is trying to merge onto. If not
specified, base will default to ``master`` branch.

The changes will be checked out locally into a branch called ``PR<number>``

Use the same command to fetch changes when the PR is updated with more commits
or when you need to change the branch.

Example:
* ``git pr-checkout origin 94`` for any PR to ``master`` branch
* ``git pr-checkout origin 94 develop`` for other branches

.. note::
    The base branch can be obtained from web UI easily. It is also possible to
    programmatically get the base branch by using the Github API but that
    requires an access token setup in the machine.
    The default base branch name can be set with 
    ``git config --add pr.defaultbase <name>``


``pr-show``
----------

Show the changes between current PR branch and the base branch.

The command lists all the commits in the PR and the files changed.


``pr-diff``
-----------

Show all the changes in the PR with ``git diff``.
Optionally supply a file path as argument to show changes of that file.

Example: ``git pr-diff src/program.c``


``pr-difftool``
---------------

Same as ``pr-diff`` but also invokes the ``git difftool`` instead.

.. tip::
    * Configure VIM as your difftool with 
      ``git config --global --add diff.tool vimdiff``
    * In case of opening without arguments to show all files, use ``:cq`` to
      stop opening other files

Example: ``git pr-difftool src/``


``pr-rmbranch``
---------------

Delete the checkout PR branch and remove the local configs set.

Example: ``git pr-rmbranch 88``
