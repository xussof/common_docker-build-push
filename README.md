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
      example1:
        #https://docs.ansible.com/ansible/latest/modules/docker_image_module.html
        #Local path where the dockerfile is placed
        path:
        #Url to registry. name: registry.ansible.com/chouseknecht/sinatra
        repository:
        #name for this image
        name:
        #Push image to registr? yes, no
        push:
        #Default: latest. Example v1
        tag:
        #build, load, pull, local
        source:


Work to do:
Need to work on role to log in to scaleway for example.

Dependencies
------------

All dependencies will appear on requirements.yml file

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    #ansible-playbook job-docker-build-push.yml --extra-vars "ansible_become_pass=sudo_pass"
    - hosts: localhost
      pre_tasks:
        - raw:  ansible-galaxy install -f -r common_docker-build-push/requirements.yml

      vars:
        #byxussofvault
        - bitbucket_password: bitbucket_pass
        - docker_img_dict:
            test-mqtt:
              #https://docs.ansible.com/ansible/latest/modules/docker_image_module.html
              #Local path where the dockerfile is placed
              path: /data/project/repos/bitbucket/gitops-helm/helm-test-mqtt
              #Url to registry. name: registry.ansible.com/chouseknecht/sinatra
              repository: repoUrlProject
              #Name for tis image
              name: test-mqtt
              #yes, no
              push: yes
              #Default: latest. Example v1
              tag: 1.0.4
              #build, load, pull, local
              source: build
            test-internal:
              #https://docs.ansible.com/ansible/latest/modules/docker_image_module.html
              #Local path where the dockerfile is placed
              path: /data/project/repos/bitbucket/gitops-helm/helm-test-internal
              #Url to registry. name: registry.ansible.com/chouseknecht/sinatra
              repository: repoUrlProject
              #Name for tis image
              name: test-internal
              #yes, no
              push: yes
              #Default: latest. Example v1
              tag: 1.0.0
              #build, load, pull, local
              source: build
      tasks:
        - name: Including role to test
          include_role:
            name: common_docker-build-push
          with_dict: "{{ docker_img_dict }}"

License
-------

BSD

Author Information
------------------
Made by @{{ author_name }}
