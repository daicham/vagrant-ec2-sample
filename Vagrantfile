# -*- mode: ruby -*-
# vi: set ft=ruby :

Dotenv.load

# change default provider to aws
ENV['VAGRANT_DEFAULT_PROVIDER'] = "aws"

Vagrant.configure(2) do |config|
  config.vm.box = "aws-dummy"
  config.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = ENV["AWS_ACCESS_KEY_ID"]
    aws.secret_access_key = ENV["AWS_SECRET_ACCESS_KEY"]
    aws.keypair_name = ENV["AWS_KEYPAIR_NAME"]

    aws.ami = "ami-cbf90ecb"
    aws.instance_type = "t2.micro"
    aws.security_groups = [ 'ssh' ]
    aws.region = "ap-northeast-1" # Tokyo

#    aws.user_data = File.read("user_data.txt")

    override.ssh.username = "ec2-user"
    override.ssh.private_key_path = ENV["SSH_PRIVATE_KEY_PATH"]
#    override.ssh.port = 443
  end
end
