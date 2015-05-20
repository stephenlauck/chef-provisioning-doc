# Setup Provisioning Node

## Manual Install
1. Install development environment
    * Debian based (apt): ``` apt-get install build-essential```
    * RHEL based (yum): ``` yum groupinstall "Development Tools"```
    * OS X: ``` xcode-select --install```

2. [Install Git](http://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
3. [Install ChefDK](https://downloads.chef.io/chef-dk/)
4. Install 'knife push': ```chef gem install knife-push```

## Cookbook for provisioning node

[chef-provisioning-node cookbook](https://github.com/stephenlauck/chef-provisioning-node)
