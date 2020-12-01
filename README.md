



### Set Up tyk server
-Provide server url in inventory file (replace inventory.template)
-Provide config info in roles/tyk/vars/main.yml (replace main.yml.template)

    $ ansible-playbook setup_tyk.yml

### Add api definitions to tyk

- Create the api definition file in api_definitions (reference template in - api_definitions/api_def)
- Create the access token file in api_definitions (reference template in - api_definitions/access_key)
template contains examples for api key auth, basic auth, url rewrite to send traffic to different backend services based on http method etc.
- Save config in roles/define_api/vars/main.yml (replace main.yml.template)
- Add required variables in placeholders inside setup_api.yml

    $ ansible-playbook setup_api.yml

### setup nginx reverse proxy to forward http traffic to tyk gateway

First replace url to redirect to, i.e. the tyk url in reverse_proxy.conf.
Also set the API_KEY as required
    $ ansible-playbook setup_nginx.yml