# Vagrant + Ansible Demo #

## 1. Vagrant

1. Start Vagrant

	```
vagrant up
```

2. Login to Vagrant VM

	```
vagrant ssh
```

3. Reboot

	```
vagrant reload
```

4. Shutdown

	```
vagrant halt
```

5. Destroy

	```
vagrant destroy
```

---

## Ansible

1. [Install Ansible](http://docs.ansible.com/intro_installation.html) on the host OS.

	```
sudo pip install ansible
```

	... on OSX
	
	```
brew install ansible
```

2. Edit `Vagrantfile`

	```
vim Vagrantfile
```

3. Uncomment these lines:

	```
config.vm.provision "ansible" do |ansible|
	ansible.playbook = "provisioning/devbox.yml"
end
```

4. Start provisioning

	```
vagrant provision
```

	or restart with provisioning:

	```
vagrant reload --provision
```

5. Install `rvm1-ansible` from [Ansible Galaxy](https://galaxy.ansible.com/list#/roles/1087).

	```
ansible-galaxy install rvm_io.rvm1-ruby
```

6. Uncomment this line from `devbox.yml`

	```
   - { role: rvm_io.rvm1-ruby, tags: ruby }
```

7. Run Ansible again.

	```
vagrant provision
```
