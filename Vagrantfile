# -*- mode: ruby -*-
# vi: set ft=ruby :
 

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.hostname = "foo10-vm"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1536"
  end
  config.vm.network :forwarded_port, guest: 27017, host: 27017, auto_correct: false
  # config.vm.network :forwarded_port, guest: 1337, host: 1337, auto_correct: false
  # config.vm.network :forwarded_port, guest: 4040, host: 4040, auto_correct: false
  config.vm.provision "docker" do |d|
    d.pull_images "mongo"
    # d.pull_images "parseplatform/parse-server"
    # d.pull_images "parseplatform/parse-dashboard"
    d.run "mongo", 
      args: "-d -p 27017:27017 --name mongodb"
    # d.run "mongo",
    #  args: "-p 27017:27017 --name mongodb -d mongo:latest --smallfiles"
    # d.run "parseplatform/parse-server",
    #  args: "--name server --link mongo -d parse-server --appId foo10app --masterKey foo10appkey --databaseURI mongodb://mongo/foo10"
    #d.run "parseplatform/parse-dashboard",
    #  args: "--name dashboard --link server:server -d -p 4040:4040 --dev --appId foo10app --masterKey foo10appkey --serverURL http://server/parse"
  end
end