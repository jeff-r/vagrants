This is a Vagrant sandbox.

Before starting the postgresql machine:

    ansible-galaxy install ANXS.postgresql
    vagrant plugin install vai

After some experimenting and blog reading, I've
separated ansible from Vagrant.

See [here](https://github.com/MatthewMi11er/vai), [here](https://github.com/debops/examples/tree/master/vagrant-multi-machine), and [here](http://blog.wjlr.org.uk/2014/12/30/multi-machine-vagrant-ansible-gotcha.html).

I had trouble getting ansible to run correctly on the machines I wanted when running from within Vagrant. This was my inexperience, and I have a guess about what I was doing wrong.

But this is easier. And this separates concerns better.

Also, Vagrant apparently doesn't allow Ansible to run in parallel, which it can do if run on its own. And there are other issues.

So use vai. Vai generates a playbook from your Vagrantfile, and then you can run ansible directly using it:

    ansible-playbook -i ansible_inventory master_playbook.yml

Next step: add code to the Sinatra apps that use data from postgresql.
