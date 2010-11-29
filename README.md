#How to get started with mvim#

* Install [macvim](http://code.google.com/p/macvim)
* git clone https://github.com/neerajdotname/vim
* cd vim
* rake

##Setup symbolic links##

    ln -s /Users/nsingh/dev/vim/vimrc ~/.vimrc
    ln -s /Users/nsingh/dev/vim/gvimrc ~/.gvimrc
    ln -s /Users/nsingh/dev/vim ~/.vim

## Installing exuberant ctags

    cd ~
    mkdir src
    cd src
    curl -O http://superb-west.dl.sourceforge.net/sourceforge/ctags/ctags-5.8.tar.gz
    tar xzvf ctags-5.8.tar.gz
    cd ctags-5.8
    ./configure
    make
    sudo make install

ctags has been installed at <tt>/usr/local/bin</tt> . However mac comes pre installed with ctags from
a different provider. In order to make sure that exuberant ctags is found first in the
path, open <tt>~/.bash_profile</tt> and add following line.

    export PATH="/usr/local/bin:$PATH"

Now let's see if exuberant ctags is properly installed.

    source ~/.bash_profile
    > ctags --version
    Exuberant Ctags 5.8, Copyright (C) 1996-2009 Darren Hiebert
      Compiled: Sep  9 2009, 11:41:52
      Addresses: <dhiebert@users.sourceforge.net>, http://ctags.sourceforge.net
      Optional compiled features: +wildcards, +regex

    cd demo
    rake rails:freeze:edge RELLEASE=2.3.5

    ctags -R --exclude=*.js

Now open project type in mvim and take cursor to validates_uniqueness_of method.
Hit <tt>ctrl ]</tt> and now you should be inside the rails code base. To get back hit <tt>ctrl t</tt> .

