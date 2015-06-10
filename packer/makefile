CHANNEL    := stable

FILES = \
	files/box/change_host_name.rb \
	files/box/configure_networks.rb \
	files/box/Vagrantfile \
	files/coreos-setup-environment \
	files/install.yml \
	files/vagrant

box: coreos.json builds/virtualbox/coreos-$(CHANNEL).box $(FILES)

builds/virtualbox/coreos-$(CHANNEL).box:
	packer build -only=virtualbox-iso coreos.json

install: builds/virtualbox/coreos-$(CHANNEL).box
	vagrant box add --force --provider=virtualbox --name deis/coreos-$(CHANNEL) builds/virtualbox/coreos-$(CHANNEL).box

clean:
	rm -fr builds
	rm -fr packer_cache

.PHONY: box clean
