# Windows��Homestead�𓱓�����
- ��{�I�Ɍ����ɂ̂��Ă���C���X�g�[�����@�Ŏ������A����Ă��Ȃ����Ƃł͂܂����_���L�ڂ���B
## Homestead.yaml���ǂ��ɂ��邩������Ȃ�
- �����ɂ́Ainit.sh�����s����Bwindows�₵�Ǝv������init.bat���������B�悩�����B�������B
## ���J���������Ƃ������L�̃G���[����������B
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
- �悭���邱�ƁB�悭���邱�ƁB���������B������΍��ׂ��B���J����Windows�ł�����݂����₯�ǁB����́Abash on Windows�ł��Ă݂�B
### bash on windows�̃C���X�g�[���J�n�I�@�ˁ@����
### bash �ɐڑ� �R�}���h�v�����v�g��bash!!����Ȋ����Ō��J�����쐬
~~~bash
ssh-keygen -t rsa -C "your@email.com"
~~~
### �ŁA�ǂ��ɍ�������킩���悤�ɂȂ�B�����ĒT���B�������B�����B
~~~bash
cd C:\Users\nishimine\AppData\Local\lxss\home\nishimine\.ssh
~~~
### �����āAhomestead.yaml��ҏW

~~~yaml
authorize: C:\Users\nishimine\AppData\Local\lxss\home\nishimine\.ssh\id_rsa.pub

keys:
    - C:\Users\nishimine\AppData\Local\lxss\home\nishimine\.ssh\id_rsa
~~~
