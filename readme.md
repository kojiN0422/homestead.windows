# WindowsにHomesteadを導入する
- 基本的に公式にのっているインストール方法で試すが、乗っていないことではまった点を記載する。

## 公開鍵が無いという下記のエラーが発生する。
~~~ruby
C:/work/localwork/lalavel/Homestead/scripts/homestead.rb:109:in `read': No such file or directory @ rb_sysopen - C:/Users/nishimine/.ssh/id_rsa (Errno::ENOENT)
        from C:/work/localwork/lalavel/Homestead/scripts/homestead.rb:109:in `block (2 levels) in configure'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/plugins/kernel_v2/config/vm_provisioner.rb:72:in `call'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/plugins/kernel_v2/config/vm_provisioner.rb:72:in `add_config'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/plugins/kernel_v2/config/vm.rb:324:in `provision'
        from C:/work/localwork/lalavel/Homestead/scripts/homestead.rb:106:in `block in configure'
        from C:/work/localwork/lalavel/Homestead/scripts/homestead.rb:105:in `each'
        from C:/work/localwork/lalavel/Homestead/scripts/homestead.rb:105:in `configure'
        from C:/work/localwork/lalavel/Homestead/Vagrantfile:30:in `block in <top (required)>'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/config/v2/loader.rb:37:in `call'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/config/v2/loader.rb:37:in `load'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/config/loader.rb:113:in `block (2 levels) in load'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/config/loader.rb:107:in `each'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/config/loader.rb:107:in `block in load'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/config/loader.rb:104:in `each'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/config/loader.rb:104:in `load'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/vagrantfile.rb:28:in `initialize'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/environment.rb:740:in `new'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/environment.rb:740:in `vagrantfile'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/environment.rb:486:in `host'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/environment.rb:208:in `block in action_runner'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/action/runner.rb:33:in `call'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/action/runner.rb:33:in `run'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/environment.rb:473:in `hook'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/lib/vagrant/environment.rb:722:in `unload'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/bin/vagrant:177:in `ensure in <main>'
        from C:/HashiCorp/Vagrant/embedded/gems/gems/vagrant-1.8.5/bin/vagrant:177:in `<main>'
~~~
- 今回は、bash on Ubuntu on Windowsを試してみる。
### bash on windowsのインストール開始！　⇒　完了
### こんな感じで公開鍵を作成
~~~bash
ssh-keygen -t rsa -C "your@email.com"
~~~
### 下記が、bash on Ubuntu on Windowsとの共有フォルダ
~~~bash
cd C:\Users\{username}\AppData\Local\lxss
~~~
### homesteadで、公開鍵は、下記のように定義されている。

~~~yaml
authorize: ~/.ssh/id_rsa.pub

keys:
    - ~/.ssh/id_rsa
~~~
- [ ~ ]ホームディレクトリは、Windowsの場合は、UserフォルダがあるストレージのUserフォルダを指し示す。
~~~
例) 
 C:\Users\{UserName}\
~~~
公開鍵は、ホームディレクトリの.sshフォルダ内に格納する。

## vagrant upで、SSH接続に失敗し続ける。

~~~bash
Bringing machine 'homestead-7' up with 'virtualbox' provider...
==> homestead-7: Importing base box 'laravel/homestead'...
==> homestead-7: Matching MAC address for NAT networking...
==> homestead-7: Checking if box 'laravel/homestead' is up to date...
==> homestead-7: Setting the name of the VM: homestead-7
The name of your virtual machine couldn't be set because VirtualBox
is reporting another VM with that name already exists. Most of the
time, this is because of an error with VirtualBox not cleaning up
properly. To fix this, verify that no VMs with that name do exist
(by opening the VirtualBox GUI). If they don't, then look at the
folder in the error message from VirtualBox below and remove it
if there isn't any information you need in there.

VirtualBox error:

VBoxManage.exe: error: Could not rename the directory 'C:\Users\nishimine\VirtualBox VMs\settler_default_1467045720829_25020_1477785209970_36885' to 'C:\Users\nishimine\VirtualBox VMs\homestead-7' to save the settings file (VERR_ALREADY_EXISTS)
VBoxManage.exe: error: Details: code E_FAIL (0x80004005), component SessionMachine, interface IMachine, callee IUnknown
VBoxManage.exe: error: Context: "SaveSettings()" at line 3052 of file VBoxManageModifyVM.cpp

C:\work\localwork\lalavel\Homestead>vagrant up
Bringing machine 'homestead-7' up with 'virtualbox' provider...
==> homestead-7: Checking if box 'laravel/homestead' is up to date...
==> homestead-7: Setting the name of the VM: homestead-7
==> homestead-7: Clearing any previously set network interfaces...
==> homestead-7: Preparing network interfaces based on configuration...
    homestead-7: Adapter 1: nat
    homestead-7: Adapter 2: hostonly
==> homestead-7: Forwarding ports...
    homestead-7: 80 (guest) => 8000 (host) (adapter 1)
    homestead-7: 443 (guest) => 44300 (host) (adapter 1)
    homestead-7: 3306 (guest) => 33060 (host) (adapter 1)
    homestead-7: 5432 (guest) => 54320 (host) (adapter 1)
    homestead-7: 22 (guest) => 2222 (host) (adapter 1)
==> homestead-7: Running 'pre-boot' VM customizations...
==> homestead-7: Booting VM...
==> homestead-7: Waiting for machine to boot. This may take a few minutes...
    homestead-7: SSH address: 127.0.0.1:2222
    homestead-7: SSH username: vagrant
    homestead-7: SSH auth method: private key
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
                                                                                                                                                                       homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
    homestead-7: Warning: Authentication failure. Retrying...
Timed out while waiting for the machine to boot. This means that
Vagrant was unable to communicate with the guest machine within
the configured ("config.vm.boot_timeout" value) time period.

If you look above, you should be able to see the error(s) that
Vagrant had when attempting to connect to the machine. These errors
are usually good hints as to what may be wrong.

If you're using a custom box, make sure that networking is properly
working and you're able to connect to the machine. It is a common
problem that networking isn't setup properly in these boxes.
Verify that authentication configurations are also setup properly,
as well.

If the box appears to be booting properly, you may want to increase
the timeout ("config.vm.boot_timeout") value.
~~~
- debug levelを[info]にしてログを確認します。
~~~bash
  set VAGRANT_LOG=info
  vagrant up 2>error.txt
~~~

- 下記のエラーを確認

~~~
 INFO ssh: Attempting SSH connection...
 INFO ssh: Attempting to connect to SSH...
 INFO ssh:   - Host: 127.0.0.1
 INFO ssh:   - Port: 2222
 INFO ssh:   - Username: vagrant
 INFO ssh:   - Password? false
 INFO ssh:   - Key Path: ["C:/Users/{username}/.vagrant.d/insecure_private_key"]
 INFO ssh: SSH not up: #<Vagrant::Errors::SSHAuthenticationFailed: SSH authentication failed! This is typically caused by the public/private
keypair for the SSH user not being properly set on the guest VM. Please
verify that the guest VM is setup with the proper public key, and that
the private key path for Vagrant is setup properly as well.>
ERROR warden: Error occurred: Guest-specific operations were attempted on a machine that is not
ready for guest communication. This should not happen and a bug
should be reported.
~~~
-  INFO ssh:   - Key Path: ["C:/Users/{username}/.vagrant.d/insecure_private_key"]　が気になりました。

- 立ち上げたゲストOSに、127.0.0.1にvagrantユーザーでログインして、.sshフォルダの公開鍵を確認。
- やはり、こちらで作成した公開鍵か登録されていなかった。手動で追加する。
- そして、公開鍵の対となる秘密鍵を使用して通信出来るように下記のように設定する。
~~~ruby
Vagrantfile
config.ssh.private_key_path = File.expand_path('../vagrant_private_key', __FILE__)
~~~
- TODO::秘密鍵の指定方法は、setting[]から取ってこれそうなので工夫する。
- 秘密鍵をvagrant_private_keyファイルとして、Vagrantfileと同じフォルダに保存する。

## homestead.yamlファイルのfolder設定を自分のプロジェクトに合わせて変更しました。

~~~yaml
folders:
    - map: ~/Code
      to: /home/vagrant/Code
~~~



