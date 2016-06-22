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
  config.vm.network "forwarded_port", guest: 8080, host: 9191
  $script = <<SCRIPT
sudo mkdir -p /opt/jbox/
sudo mkdir -p /opt/jbox/script/
sudo apt-get install -y git
sudo echo 'alias jbox="/opt/jbox/script/jira-box/jbox"' >> ~/.profile
sudo rm -rf /opt/jbox/script/jira-box
cd /opt/jbox/script/
sudo git clone https://bitbucket.org/atlassian/jira-box.git
sudo chown vagrant:vagrant -R /opt/jbox/
SCRIPT

      config.vm.provision :shell, :inline => $script

end