# WindowsにHomesteadを導入する
- 基本的に公式にのっているインストール方法で試すが、乗っていないことではまった点を記載する。
## Homestead.yamlがどこにあるか分からない
- 公式には、init.shを実行せよ。windowsやしと思ったらinit.batがあった。よかった。さすが。
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
- よくあること。よくあること。慣れっこよ。無ければ作るべし。公開鍵はWindowsでも作れるみたいやけど。今回は、bash on Windowsでしてみる。
### bash on windowsのインストール開始！　⇒　完了
### bash に接続 コマンドプロンプトでbash!!こんな感じで公開鍵を作成
~~~bash
ssh-keygen -t rsa -C "your@email.com"
~~~
### で、どこに作ったかわからんようになる。そして探す。あった。ここ。
~~~bash
cd C:\Users\nishimine\AppData\Local\lxss\home\nishimine\.ssh
~~~
### そして、homestead.yamlを編集

~~~yaml
authorize: C:\Users\nishimine\AppData\Local\lxss\home\nishimine\.ssh\id_rsa.pub

keys:
    - C:\Users\nishimine\AppData\Local\lxss\home\nishimine\.ssh\id_rsa
~~~
