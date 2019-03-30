Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"

  config.vm.provider :virtualbox do |vb|
    vb.name = 'atompm'
    vb.gui = false
    vb.memory = 4096
    vb.cpus = 2
  end

  config.vm.network :forwarded_port, guest: 8124, host: 8124
  config.vm.network :forwarded_port, guest: 8125, host: 8125
  config.vm.network :forwarded_port, guest: 80, host: 80

  config.vm.provision "shell", inline: "apt-get install sshpass", privileged: true

  $script = <<-SCRIPT
  echo "INSTALLING NECESSARY PROGRAMS"
  sudo apt-get update
  sudo apt-get install -y python-pip
  sudo apt install -y build-essential python-dev libxml2 libxml2-dev zlib1g-dev
  pip install python-igraph
  pip install six
  curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
  sudo apt-get install -y nodejs
  sudo apt-get install -y npm
  sudo apt-get install -y unzip
  SCRIPT
  config.vm.provision "shell", inline: $script, privileged: false 


  $script = <<-SCRIPT
  echo "INSTALLING ATOMPM"
  cd /home/vagrant
  wget https://github.com/AToMPM/atompm/archive/v0.8.1.zip
  unzip v0.8.1.zip
  cd atompm-0.8.1
  npm install --production
  cd /home/vagrant/atompm-0.8.1
  echo -e "killall -9 python\nkillall -9 nodejs\nnodejs httpwsd.js &\nsleep 3\npython mt/main.py &echo 'AToMPM should be running succesfully now. Browse to http://localhost:8124/atompm now.'" > run.sh
  chmod +x run.sh
  SCRIPT
  config.vm.provision "shell", inline: $script, privileged: false 

  config.vm.post_up_message = "
  ************************************************
  ************************************************
                      Notes
  ************************************************
  ************************************************
  - AToMPM is installed now. To run it, you should ssh into vagrant using 'vagrant ssh' command.

  IN THE VIRTUAL MACHINE AFTER SSH'ED INTO BY USING THE COMMAND ABOVE.
  - To run AToMPM, go to 'atompm-0.8.1' folder.
        > cd atompm-0.8.1
  - And run 'run.sh'
        > ./run.sh
  "
end