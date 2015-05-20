# Set up Chef Provisioning repo

```
chef generate repo provisioning-repo
cd provisioning-repo
mkdir .chef
```
### create provisioning-repo/.chef/knife.rb

```
current_dir = File.dirname(__FILE__)
log_level                :info
log_location             STDOUT
node_name                "example"
client_key               "#{current_dir}/example.pem"
# chef_server_url          'chefzero://localhost:8889'
cache_type               'BasicFile'
cache_options( :path => "#{ENV['HOME']}/.chef/checksums" )
cookbook_path            "#{current_dir}/../cookbooks"
```

### create provisioning-repo/Berksfile

```
source "https://supermarket.chef.io"

cookbook 'chef-server-provision',
  git: 'https://github.com/stephenlauck/chef-server-provision.git'
```

### create provisioning-repo/Gemfile

```
source 'https://rubygems.org'

gem 'chef-provisioning'
gem 'chef-provisioning-aws'
gem 'chef-provisioning-vagrant'

gem 'berkshelf'
```

### install gems and cookbooks
```
bundle install
bundle exec berks install
```

### vendor cookbooks
```
bundle exec berks vendor cookbooks
```

### run provisioning recipe with chef-client in local mode to create node
```
bundle exec chef-client -z -o chef-server-provision::default
```

### run recipe to destroy
```
bundle exec chef-client -z -o chef-server-provision::destroy_all
```
