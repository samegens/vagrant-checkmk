$server_provision_script = <<-SCRIPT
wget https://checkmk.com/support/1.5.0p19/check-mk-raw-1.5.0p19_0.bionic_amd64.deb -O /tmp/checkmk.deb
apt install -y /tmp/checkmk.deb
omd create mysite
omd start mysite
# You can now open the site at http://192.168.33.10/mysite, log in with cmkadmin and the password shown by 'omd create mysite'.
SCRIPT

$host_provision_script = <<-SCRIPT
apt-get update
apt-get install -y xinetd
apt install -y /vagrant/check-mk-agent_1.5.0p19-b45542ef3fc77240_all.deb
SCRIPT

Vagrant.configure("2") do |config|
	config.vm.define "checkmkserver" do |checkmkserver|
		checkmkserver.vm.box = "ubuntu/bionic64"
		checkmkserver.vm.hostname = "checkmkserver"
		checkmkserver.vm.network "private_network", ip: "192.168.33.10"
		checkmkserver.vm.provision "shell", inline: $server_provision_script
	end

	config.vm.define "checkmkhost" do |checkmkhost|
		checkmkhost.vm.box = "ubuntu/bionic64"
		checkmkhost.vm.hostname = "checkmkhost"
		checkmkhost.vm.network "private_network", ip: "192.168.33.20"
		checkmkhost.vm.provision "shell", inline: $host_provision_script
	end
end
