# The repo contains Packer that build an GCP Image with Consul client - the Image is "ubuntu-1804-lts" based with latest updates.
### This will build an GCP Image with [Consul](https://www.consul.io/) client installed . 

## Usage example:

- Install [Packer](https://www.packer.io/)
- Setup your [gcloud command-line tool](https://cloud.google.com/sdk/)
- If you need the latest version of Consul - from your CLI execute a following command:

```
packer build client.json
``` 
If you need specific version 
```
packer build -var 'CONSUL=1.4.2' client.json
``` 

For more info please check a following link:

https://www.packer.io/intro/getting-started/build-image.html#some-more-examples-

To test you will need Kitchen:

Kitchen is a RubyGem so please find how to install and setup Test Kitchen for developing infrastructure code, check out the [Getting Started Guide](http://kitchen.ci/docs/getting-started/).

A needed [gems](https://guides.rubygems.org/what-is-a-gem/) are in your Gemfile just install them:

```
bundle install
```
Than simply execute a following commands:

```
bundle kitchen converge
bundle kitchen verify
bundle kitchen destroy
```
The result should be as follow
``` 
  ✔  operating_system: Command: `lsb_release -a`
     ✔  Command: `lsb_release -a` stdout should match /Ubuntu/

  File /usr/local/bin/consul
     ✔  should exist
  File /etc/systemd/system/consul.service
     ✔  should exist

Profile Summary: 1 successful control, 0 control failures, 0 controls skipped
Test Summary: 3 successful, 0 failures, 0 skipped
       Finished verifying <default-ubuntu> (0m6.72s).
```
