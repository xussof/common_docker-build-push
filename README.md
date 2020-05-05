common_docker-build-push

=========

This role will build and push a docker image to the selected registry.

Requirements
------------

All dependencies will appear on requirements.yml file

Role Variables
--------------
#Example on how to call this role
#docker_img_dict:
#  example1:
#    #https://docs.ansible.com/ansible/latest/modules/docker_image_module.html
#    #Local path where the dockerfile is placed
#    path:
#    #Url to registry. name: registry.ansible.com/chouseknecht/sinatra
#    repository:
#    #name for this image
#    name:
#    #Push image to registr? yes, no
#    push:
#    #Default: latest. Example v1
#    tag:
#    #build, load, pull, local
#    source:

Work to do:
Need to work on role to log in to scaleway for example.

Dependencies
------------

All dependencies will appear on requirements.yml file

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: xussof.common_docker-build-push }

License
-------

BSD

Author Information
------------------
Made by @xussof
