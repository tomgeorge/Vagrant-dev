#Vagrantfile-dev#

This is my Vagrantfile that has a nice dev setup for me.

+ ubunu/trusty64 box
+ VBox gui is true because I'm paranoid
+ zsh/oh-my-zsh
+ git config
+ tmux with Ctrl+a
+ vi with a whole bunch of plugins (see my [.vimrc](http://stash.paychex.com/users/tgeorge/repos/dotfiles/browse/vim/.vimrc))
+ docker


#Usage#

`vagrant up`

The terminal will go all weird, because of the call to `vi +PluginInstall +qall`.  You should be able to get everything back to normal with a `clear` command.

`vagrant ssh`  