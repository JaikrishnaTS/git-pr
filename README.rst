git-pr
######

``git-pr`` is a set of git commands built to locally checkout and view/test 
Github Pull Requests.

Installation
============

Clone the repository and copy the contents of the ``bin/`` directory to 
``.local/bin`` or anywhere in your ``$PATH``.

``mkdir -p .local/bin; cp -r bin/* .local/bin/``

Commands
========

The tool contains the following commands

``pr-checkout <remote> <base> <PR number>``
-------------------------------------------

Checkout the PR number ``<PR number>`` from repository at ``<remote>``.
The ``<base>`` is the base branch that the PR is trying to merge onto. 

.. note::
    The base branch can be obtained from web UI easily. It is also possible to
    programmatically get the base branch by using the Github API but that
    requires an access token setup in the machine.

Example: ``git pr-checkout origin master 94``
