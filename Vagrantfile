# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements. See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License. You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  # ubuntu/trusty64 Official Ubuntu Server 14.04 LTS (Trusty Tahr) builds
  config.vm.box = "ubuntu/trusty64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  #config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine.

  # Forward local host port 8080 to zeppelin port 8080
  # Forward local host port 4040 to spark UI port 4040
  # Forward local host port 4000 to jekyll documentation port 4000
  # comment out the following lines to use a fixed IP
  config.vm.network "forwarded_port", guest: 8080, host: 8001
  config.vm.network "forwarded_port", guest: 4040, host: 4040
  config.vm.network "forwarded_port", guest: 4000, host: 4000


  # Uncomment to create a private network, which allows access to the machine
  # using a specific IP.  Port forwarding not required in this case.
  # Select an address range based on a free block available
  # in your network environment.  192.168.x.x is an example
  #config.vm.network "private_network", ip: "192.168.51.52"

  # Set the hostname.  Comment this out if you don't want the hostname managed by the VM
  config.vm.hostname = "zeppelinvm"

  # Modify the number of CPUs and memory used by the VM
  # by adjusting
  #   --memory
  # and uncommenting and/or updating
  #   --cpus

  config.vm.provider "virtualbox" do |vb|
     vb.customize ["modifyvm", :id, "--memory", "2048"]
     #vb.customize ["modifyvm", :id, "--cpus", "2"]
     vb.name = "zeppelinvm"
  end

  config.vm.provision "ansible" do |ansible|
     ansible.playbook = "ansible-roles.yml"
  end

  config.vm.provision "shell", path: "show-instructions.sh", run: "always"

end
