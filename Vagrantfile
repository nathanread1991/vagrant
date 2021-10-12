Vagrant.configure("2") do |config|
  config.vm.box = "peru/ubuntu-20.04-desktop-amd64"

  config.vm.provider :virtualbox do |v|
    v.gui = true
    v.memory = 4000
  end

  # Currently "ubuntu/bionic64" on VirtualBox requires `type: "virtualbox"`
  # to make synced folder works.
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

  # Add Google Chrome repository
  config.vm.provision :shell, inline: "wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub|sudo apt-key add -"
  config.vm.provision :shell, inline: "sudo sh -c 'echo \"deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main\" > /etc/apt/sources.list.d/google.list'"

  # Update repositories
  config.vm.provision :shell, inline: "sudo apt update -y"

  # Upgrade installed packages
  config.vm.provision :shell, inline: "sudo apt upgrade -y"

  # Add desktop environment
  #config.vm.provision :shell, inline: "sudo apt install -y --no-install-recommends ubuntu-desktop"
  #config.vm.provision :shell, inline: "sudo apt install -y --no-install-recommends virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11"
  # Add `vagrant` to Administrator
  config.vm.provision :shell, inline: "sudo usermod -a -G sudo vagrant"

  # Add Google Chrome
  config.vm.provision :shell, inline: "sudo apt install -y google-chrome-stable"

  # Add Chromium
  config.vm.provision :shell, inline: "sudo apt install -y chromium-browser"

  # Add Firefox
  config.vm.provision :shell, inline: "sudo apt install -y firefox"
  
  config.vm.provision :shell, inline: "sudo ln -s /usr/bin/python3.8 /usr/bin/python"
  
  config.vm.provision :shell, inline: "sudo apt install -y python3-pip"
  
  config.vm.provision :shell, inline: "sudo add-apt-repository --yes --update ppa:ansible/ansible"
 
  config.vm.provision :shell, inline: "sudo apt install -y ansible"
  
  config.vm.provision :shell, inline: "sudo pip3 install \"ansible-lint[core,community,yamllint]\""
  
  config.vm.provision :shell, inline: "snap install --classic code"
  
  config.vm.provision :shell, inline: "code --install-extension tomaciazek.ansible --user-data-dir=~"
  
    
end
