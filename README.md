# atompm-vagrant

This is a vagrant configuration file to install the necessary stuff for [AToMPM](https://github.com/atompm/atompm).

## Prerequisites

- Download and install [VirtualBox](https://www.virtualbox.org/).
- Download and install [Vagrant](https://www.vagrantup.com/).

## Initialize virtual machine

- Clone this repository
- Initialize the virtual machine
  - `> vagrant up`
  
## Run AToMPM

- SSH into vagrant virtual machine
  - `> vagrant ssh`
- CD into the atompm folder
  - `> cd atompm-0.8.1`
- Run the script
  - `> ./run.sh`
- Browse to `http://localhost:8124/atompm`
