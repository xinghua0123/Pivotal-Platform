## Pre-Requisites
### PKS Cli
Download and install the Pivotal Container Service Command Line Interface (PKS CLI):
https://network.pivotal.io/products/pivotal-container-service<br/>
After renaming the file to pks, move it to /usr/local/bin and make sure /usr/local/bin is included in the PATH.

### Root CA Certificate (if you are accessing from your localhost )
1. SSH into Ops Manager VM
2. Navigate to /var/tempest/workspaces/default/root_ca_certificate
3. Copy the content of certificate and move it to local

### UAAC Cli
Before installing UAAC Cli, make sure you have latest version of ruby. If not, please follow the steps below.
If you're on macOS, we recommend installing rbenv with Homebrew.
1. Install rbenv.
```shell
brew install rbenv
```
Note that this also installs ruby-build, so you'll be ready to install other Ruby versions out of the box.

2. Set up rbenv in your shell.
```shell
rbenv init
```

3. Close your Terminal window and open a new one so your changes take effect.

4. Verify that rbenv is properly set up using this rbenv-doctor script:
```shell
xhua@Ron-MBP   ~  curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
Checking for `rbenv' in PATH: /usr/local/bin/rbenv
Checking for rbenv shims in PATH: OK
Checking `rbenv install' support: /usr/local/bin/rbenv-install (ruby-build 20200224)
Counting installed Ruby versions: 1 versions
Checking RubyGems settings: OK
Auditing installed plugins: OK
```

5. Now you're ready to install some other Ruby versions using:
```shell
rbenv install -l    # list out all the available version of ruby
rbenv install 2.7.0 # install the version of 2.7.0
rbenv global 2.7.0  # switch the ruby version to newly installed one
ruby --version      # verify the ruby verion
```
