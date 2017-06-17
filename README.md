# About This Repo #
This is a personal repo for setting up a freshly install Ubuntu Gnome
desktop machine (currently 16.04). If you find is useful as a starting
point for your own preferred setup ... then great !

This repo is based on this skeleton Ansible setup: https://github.com/mattjbarlow/ansible-directory

# Installing Ansible in a virtualenv #

```
sudo apt install python-pip python-setuptools virtualenv libffi-dev libssl-dev git

virtualenv ~/.virtualenvs/ansible
source ~/.virtualenvs/ansible/bin/activate
pip install -U pip
pip install -U ansible
# Or, use the latest dev version of Ansible from Github
# pip install -U git+git://github.com/ansible/ansible.git@devel
```

# Running the workstation playbook against localhost #

```
ansible-playbook -K -b -c local -i workstations workstations.yml
```

# Running the workstation playbook against localhost #

```
ansible-galaxy install -r requirements.yml
ansible-playbook -K -b -c local -i workstations workstations.yml
```

# Adding a new role #
In your roles directory, type `ansible-galaxy init some_role_name` in order to generate an empty skeleton for a new role you are working on.

Example:
```
ansible-galaxy init nginx
```

Check out [Ansible Examples](https://github.com/ansible/ansible-examples) for example playbooks.

# Best Practices Directory Layout #

Based on [Ansible Best Practices](https://docs.ansible.com/ansible/playbooks_best_practices.html#directory-layout)
As implemented by: https://github.com/mattjbarlow/ansible-directory

```
production                # inventory file for production servers
staging                   # inventory file for staging environment

group_vars/
   group1                 # here we assign variables to particular groups
   group2                 # ""
host_vars/
   hostname1              # if systems need specific variables, put them here
   hostname2              # ""

library/                  # if any custom modules, put them here (optional)
filter_plugins/           # if any custom filter plugins, put them here (optional)

site.yml                  # master playbook
webservers.yml            # playbook for webserver tier
dbservers.yml             # playbook for dbserver tier

roles/
    common/               # this hierarchy represents a "role"
        tasks/            #
            main.yml      #  <-- tasks file can include smaller files if warranted
        handlers/         #
            main.yml      #  <-- handlers file
        templates/        #  <-- files for use with the template resource
            ntp.conf.j2   #  <------- templates end in .j2
        files/            #
            bar.txt       #  <-- files for use with the copy resource
            foo.sh        #  <-- script files for use with the script resource
        vars/             #
            main.yml      #  <-- variables associated with this role
        defaults/         #
            main.yml      #  <-- default lower priority variables for this role
        meta/             #
            main.yml      #  <-- role dependencies

    webtier/              # same kind of structure as "common" was above, done for the webtier role
    monitoring/           # ""
    fooapp/               # ""
```

