### Windows Containers and Ansible (experimental)

This branch contains code that allow Ansible to remotely manage Windows Containers. In short, you need a hosts file looking something like this:

```
[all]

[all:vars]
ansible_password=Secrit123
ansible_user=Administrator
ansible_winrm_server_cert_validation=ignore

[windows_client]
awsregular ansible_host=10.245.8.26 ansible_connection=winrm
awscontainer ansible_host=10.245.8.26 ansible_connection=winrm_containers containerid=62fcc2dd1951862f562cba44b7830a7fac73eeb2b0d7192c58d3a467e902143f
```

The two entries above control the same host, but the latter will proxy any Ansible command/module into the running container with the given id.
Expect many of the current Powershell-based Ansible modules to fail when run inside a Container!