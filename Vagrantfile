VAGRANTFILE_API_VERSION = "2"
box      = 'ubuntu/trusty64'
url      = 'https://atlas.hashicorp.com/ubuntu/boxes/trusty64'
hostname = 'jira'
ip       = '192.168.5.99'
ram      = '1024'

Vagrant::Config.run do |config|
  config.vm.box = box
  config.vm.box_url = url
  config.vm.host_name = hostname
  config.vm.network :hostonly, ip 

  config.vm.customize [
    'modifyvm', :id,
    '--name', hostname,
    '--memory', ram
  ]
end

Vagrant.configure("2") do |config|
  config.vm.network "forwarded_port", guest: 8005, host: 8005
  config.vm.network "forwarded_port", guest: 8080, host: 8081
  $script = <<SCRIPT
  wget https://www.atlassian.com/software/jira/downloads/binary/atlassian-jira-software-7.1.8-jira-7.1.8-x64.bin
  chmod +x atlassian-jira-software-7.1.8-jira-7.1.8-x64.bin
  sudo ./atlassian-jira-software-7.1.8-jira-7.1.8-x64.bin -q
SCRIPT

      config.vm.provision :shell, :inline => $script

end