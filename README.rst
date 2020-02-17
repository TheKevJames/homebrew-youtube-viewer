youtube-viewer Formula for Brew
===============================

This formula can be used to easily install `youtube-viewer`_ with `brew`_.

Installation
------------

.. code-block:: console

    brew install thekevjames/youtube-viewer/youtube-viewer

Note that the above is shorthand for the following two commands, if you want
to handle 'em differently:

.. code-block:: console

    brew tap thekevjames/youtube-viewer
    brew install youtube-viewer

Updating
--------

It should "Just Work" with the normal ``brew`` procedure, eg.

.. code-block:: console

    brew upgrade youtube-viewer

Why a Tap?
----------

At some point, I'll get around to including this directly in `homebrew-core`_.
They've asked I `write functional tests`_ against the YouTube API before this
can be merged -- which is totally reasonable, but since 99% of my motivation
is just to be able to use this myself and its not even my project in the first
place...

Maintaining
-----------

.. note::

    This section is mostly just a reminder for myself, feel free to ignore!

To update a new version:

.. code-block:: console

    sed -i '' 's/3.5.6/3.7.4/g' Formula/youtube-viewer.rb
    curl -Lo foo.tar.gz https://github.com/trizen/youtube-viewer/archive/3.7.4.tar.gz
    sha=$(shasum -a 256 foo.tar.gz | cut -d' ' -f1)
    rm foo.tar.gz
    sed -i '' '5s/  sha256 ".*"/  sha256 "'"${sha}"'"/' Formula/youtube-viewer.rb

    brew upgrade --debug Formula/youtube-viewer.rb

    git add Formula/youtube-viewer.rb
    git commit -m 'chore: bump version'
    git push

.. _brew: https://brew.sh/
.. _homebrew-core: https://github.com/Homebrew/homebrew-core
.. _write functional tests: https://github.com/Homebrew/homebrew-core/pull/43254
.. _youtube-viewer: https://github.com/trizen/youtube-viewer
