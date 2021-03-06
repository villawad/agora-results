# Introduction

Piece of software that processes a tally and given a pipeline it modifies the results. This is useful for example to post-process a tally to:
 - resolve tie-breaks (there can be many different algorithms to do that)
 - apply egalitarian criteria for men and women (sometimes this is even legaly mandated)
 - sort the winners of stv (which by default doesn't sort winners, just elect them)
 - other complex post-processing, like using the result of question 1 to select the first winner and then using the results of question 2 to sort the rest of the winners

# Installation

Just execute this (no stable release yet):

    $ mkvirtualenv agora-results -p $(which python3)
    $ workon agora-results
    $ pip install git+https://github.com/agoravoting/agora-results.git

# Usage

    $ agora-results --tally tally.tar.gz --config agora_tongo.test_config

Or the same shorter:

    $ agora-results -t tally.tar.gz -c config.json

# Configuration file

Configuration file specifies the pipeline of functions to be applied to the results. This is an example configuration file (yes just one variable for the pipeline, at least for now):

    [
        [
          "agora_results.pipes.results.do_tallies",
          {"ignore_invalid_votes": true}
        ]
    ]

# Available pipes

Available pipes are documented in python, in the agora_results/pipes directory.

# Development

You can of course take a look at the available pipes in the agora_results/pipes/ subdirectory and see how to develop your own pipe. Be careful, you might cook the results in an unexpected way!

This software is in development state, that's why we haven't released any stable version yet. Patches and new pipes are welcome. We will review the pipe so that it does what is expected.

# More

You can see all the available commands with:

    $ agora-results --help

You can contact us at agora-voting@googlegroups.com mailing list or at #agoravoting freenode.net channel.
