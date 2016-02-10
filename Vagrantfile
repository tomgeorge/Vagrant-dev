# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
   config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
      vb.gui = true
   end

   # install stuff
   config.vm.provision "shell", inline: "sudo apt-get update && sudo apt-get install -y wget zsh git"
   # pull down my vim stuff and set permissions
   config.vm.provision "shell", inline: "git clone https://github.com/tomgeorge/vimfiles /home/vagrant/.vim"
   config.vm.provision "shell", inline: "chown -R vagrant:vagrant /home/vagrant/.vim"

   # pull down my dotfiles and set permissions, could just use privileged: false
   config.vm.provision "shell", inline: "git clone https://github.com/tomgeorge/dotfiles /home/vagrant/dotfiles"
   config.vm.provision "shell", inline: "chown -R vagrant:vagrant /home/vagrant/dotfiles"

   # symlink my dotfiles
   config.vm.provision "shell", inline: "rm /home/vagrant/.bashrc"
   config.vm.provision "shell", inline: "ln /home/vagrant/dotfiles/zsh/.zshrc /home/vagrant/.zshrc && ln /home/vagrant/dotfiles/tmux/.tmux.conf /home/vagrant/.tmux.conf && ln /home/vagrant/dotfiles/vim/.vimrc /home/vagrant/.vimrc && ln /home/vagrant/dotfiles/bash/.bashrc /home/vagrant/.bashrc  && ln /home/vagrant/dotfiles/git/.gitconfig /home/vagrant/.gitconfig"

   # install oh-my-zsh
   config.vm.provision "shell", privileged: false,
   	inline: "git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh"
   config.vm.provision "shell", inline: "chsh -s /bin/zsh vagrant"
	
   # install vim plugins
   config.vm.provision "shell", privileged: false,
   	inline: "vi +PluginInstall +qall"

   # install docker
   config.vm.provision "docker"
   # create docker group
   config.vm.provision "shell", inline: "sudo gpasswd -a vagrant docker"
   config.ssh.forward_agent = true

   # forward port 8080
   config.vm.network "forwarded_port", guest: 8080, host: 8080 
end