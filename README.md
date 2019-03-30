# atompm-vagrant

This is a vagrant configuration file to install the necessary stuff for [AToMPM](https://github.com/atompm/atompm).

## Prerequisites

- Download and install [VirtualBox](https://www.virtualbox.org/).
- Download and install [Vagrant](https://www.vagrantup.com/).

_**Warning:** If Vagrant installer didn't alreay do it, you must put the folder that has 'vagrant' executable in your environment variables or PATH to execute the following commands._

## Initialize virtual machine

- Clone this repository
- Initialize the virtual machine (command line)
  - `> vagrant up`
  
## Run AToMPM

- SSH into vagrant virtual machine (command line)
  - `> vagrant ssh`
- CD into the atompm folder (command line)
  - `> cd atompm-0.8.1`
- Run the script (command line)
  - `> ./run.sh`
- Browse to `http://localhost:8124/atompm`


