#### <i class="icon-anchor"></i>参考

 - http://www.idcf.jp/blog/cloud/chef-11/
 - http://docs.opscode.com/install_workstation.html
 - http://dev.classmethod.jp/server-side/add-node-run-recipe/
 - http://qiita.com/satoyusuke/items/c3e66e27c3cf9d4c27d3
 - http://dotinstall.com/lessons/basic_chef/24212

**********

#### <i class="icon-anchor"></i>chef server
> 安装

    # wget https://opscode-omnibus-packages.s3.amazonaws.com/el/6/x86_64/chef-server-11.0.8-1.el6.x86_64.rpm
    # rpm -ivh chef-server-11.0.8-1.el6.x86_64.rpm

> 先要设定host名

    # hostname
    chef.dreamarts.co.jp
    # cat /etc/hosts
    175.184.44.109 chef.dreamarts.co.jp

> 设定

    # chef-server-ctl reconfigure
    https://175.184.44.109/users/login
    admin / mu6bXpiG
    
**********

#### <i class="icon-anchor"></i>chef client

>  创建空的工作目录(repository)

    # git clone git://github.com/opscode/chef-repo.git

>  拷贝chef-server的秘钥

    # mkdir /opt/chef-repo/.chef
    拷贝 ChefServer:/etc/chef-server目录下的 admin.pem, chef-validator.pem 到.chef目录下

>  安装chef client

    # curl -L https://www.opscode.com/chef/install.sh | bash

>  初始化

    # knife configure --initial
	WARNING: No knife configuration file found
	Where should I put the config file? [/root/.chef/knife.rb] /opt/chef-repo/.chef/knife.rb
	Please enter the chef server URL: [https://localhost:443] https://chef.dreamarts.co.jp
	Please enter a name for the new user: [root] li
	Please enter the existing admin name: [admin]
	Please enter the location of the existing admin's private key: [/etc/chef-server/admin.pem] /opt/chef-repo/.chef/admin.pem
	Please enter the validation clientname: [chef-validator]
	Please enter the location of the validation key: [/etc/chef-server/chef-validator.pem] /opt/chef-repo/.chef/chef-validator.pem
	Please enter the path to a chef repository (or leave blank): /opt/chef-repo
	Creating initial API user...
	Please enter a password for the new user:
	Created user[li]
	Configuration file written to /opt/chef-repo/.chef/knife.rb

> 确认

    # knife client list
    # knife user list

**********

#### <i class="icon-anchor"></i>node

> 想使用bootstrap，因为pem文件设定有passphrase而失败， 这里的-i参数指定会导致 ERROR:
> ArgumentError: Could not parse PKey: no start line错误

    # knife bootstrap test.dreamarts.co.jp -x root -i /root/dacssh_private.pem -d centos6 -r 'recipe[chef-client::delete_validation]'

> 手动安装

    # mkdir /etc/chef && cd /etc/chef
    # knife configure client -s https://chef.dreamarts.co.jp ./

> 拷贝chef_validation.pm 内容到 validation.pm中

> 将node登陆到server
    # chef-client -c client.rb
    
**********

#### <i class="icon-anchor"></i>cookbook

> 创建

    # knife cookbook create yukariap

> 安装

    # knife cookbook site install yumrepo
    http://community.opscode.com/cookbooks/yumrepo

> 上传

    # knife cookbook upload yum
    # knife cookbook upload yumrepo

> 添加run_list

    add run list
    # knife node run_list add test "recipe[yum::epel]"
