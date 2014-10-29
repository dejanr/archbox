Workstation
===========

Is a box with some operating system and personal tools needeed to do the job.

As of recently i have been mostly using mbp 13", most of ther recipes
would be aligned against this configuration. But you are free to fork
and adopt it to your will. I hope this give a good starting point.

To build this workstation i used vagrant and ansible, so if you are not
interested in starting a clean with this setup.  You could just checkout
how everything works within virtualbox.

Testing inside vagrant box
----------------

To stay up to date and try new releases, i have used packer to build basebox.

```bash
$ git clone https://github.com/elasticdog/packer-arch.git
$ cd packer-arch/
$ packer build -only=virtualbox-iso arch-template.json
$ vagrant box add arch packer_arch_virtualbox.box
```

So we could now boot up a vagrant machine and ssh inside

```bash
$ vagrant up
$ vagrant ssh
```

Starting on clean slate machine
-------------------------------

Setup dependencies, and symlink python2

```bash
$ sudo pacman -S python2
$ sudo pacman -S ansible
$ sudo ln -s /usr/bin/python2 /usr/bin/python
```

Run provision:

```bash
$ ansible-playbook -i inventory/hosts archbox.yml
```
