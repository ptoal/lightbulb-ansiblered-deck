[![GoKEV](http://GoKEV.com/GoKEV200.png)](http://GoKEV.com/)

<div style="position: absolute; top: 40px; left: 200px;">

# lightbulb-ansiblered-deck

This project is the "Ansible Red" deck HTML content.  Optionally, a daemon will be started up if you don't exclude tag "phpdaemon"


## Example Playbooks
Here's an example of how you could launch this role and deploy the PHP daemon to start on port `php_port`:
<pre>
ansible-playbook -i ec2.hosts GoKEV-lab-provision.yml --tags=phpdaemon
</pre>

Here's an example of how you could launch this role and and not start the PHP daemon (only synch the content).
The default method uses `tags: [ 'never', 'phpdaemon' ]` and only includes `phpdaemon` components when specifically invoked.  Therefore, the default nature of this role will ONLY synch content and not start the PHP web service.
<pre>
ansible-playbook -i ec2.hosts GoKEV-lab-provision.yml 
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


## Stuff still needing to be done
  - Inside `index.php` there are variables for the github star and download counts... probably should be converted to vars in defaults or `extra_vars` params
  - Certain presenters have requested dynamic ways to exclude certain sections (exclude entire dir `010_topic_that_bores_my_audience`)

## Easter Eggs
*  Not implemented, but capable:  Each directory in `html_slides` can have a `labs` directory.  Slides in this dir will automatically be presented as LABS at the end of each section (numbered directory) and presented with a gray intro slide when the deck advances past the topic section.
    * example:  `html_slides/123_some_topic/labs/00_lab1.html`
*  Troubleshooting:  See what files are being included by running a dry run:
    * `http://ansible.red/deck-ansible/?dryrun`
    * other variables that can be fed into the URL:
        * `person=someone-name` (if that person has a preferences file, context will switch to it)
        * `labs` (no value is required - simply passing this empty variable forces labs-only display mode and will not show the deck
        * `nolabs` (no value is required - opposite of `labs`, this variable forces deck-only display mode and will not show the labs
        * without `labs` or `nolabs` the default behavior is to show labs at the end of each section.

## Notes
  - index.php includes a lot of stuff as dynamic files from the html_slides directory
  - any file or dir inside `html_slides` can be excluded by starting it with an underscore
  - example:  `html_slides/_000_skipping_this_section`
  - example:  `html_slides/001_not_kipping_this_section/_skipping_this_slide.html`

## Author
  - Adapted by [Kevin Holmes](http://GoKEV.com/) from the original lightbulb workshop deck, split into dynamic individual slides

## Changelog
  - This project was first committed November 1, 2018 by [Kevin Holmes](http://GoKEV.com/).


