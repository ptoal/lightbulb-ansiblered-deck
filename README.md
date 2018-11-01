[![GoKEV](http://GoKEV.com/GoKEV200.png)](http://GoKEV.com/)

<div style="position: absolute; top: 40px; left: 200px;">

# lightbulb-ansiblered-deck

This project is the "Ansible Red" deck HTML content.  Optionally, a daemon will be started up if you don't exclude tag "phpdaemon"


## Example Playbooks
Here's an example of how you could launch this role and deploy the PHP daemon to start on port `php_port`:
<pre>
ansible-playbook -i ec2.hosts GoKEV-lab-provision.yml
</pre>

Here's an example of how you could launch this role and and not start the PHP daemon (only synch the content)
<pre>
ansible-playbook -i ec2.hosts GoKEV-lab-provision.yml --skip-tags=phpdaemon
</pre>


## Here's an example of the playbook

<pre>
---
- name: Deploy the Ansible Red deck and run it as a daemon
  hosts: myserver

  vars:
    workshop_web_path: /ansible-php-content/
    workshop_image: images/ansible-logo.png
    workshop_name: Ansible Essentials Workshop
    workshop_presenter: Demo McDemoson
    workshop_title: Solution Architect, Red Hat
    workshop_message: my email and contact info
    php_port: 8000

  roles:
    - lightbulb-ansiblered-deck

</pre>


## Troubleshooting & Improvements

- Not enough testing yet

## Notes
  - index.php includes a lot of stuff as dynamic files from the html_slides directory
  - any file or dir inside html_slides can be excluded by starting it with an underscore
  - example:  html_slides/_000_skipping_this_section
  - example:  html_slides/001_not_kipping_this_section/_skipping_this_slide.html

## Author
  - Adapted from the original lightbulb workshop deck, split into dynamic individual slides

## Changelog
  - This project was first committed November 1, 2018 by [Kevin Holmes](http://GoKEV.com/).


