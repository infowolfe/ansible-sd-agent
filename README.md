###infowolfe.sd-agent

[Server Density] is a cloud based monitoring service providing cloud management, site/app checks and instance monitoring. Its Python based agent is relatively simple, very configurable and trivially extended by the use of either paid or home-rolled plugins. This [Ansible] role is for deploying the [Server Density] agent from within your playbook.

### Installation

This role requires [Ansible] >= 1.5

### Requirements

Warning: this role uses the 'uri' module, which depends on httplib2, which will be installed automatically for you.

### Role Variables

At the moment, only 2 variables are required to be set. This section may expand in the future to include more.

```yaml
---
sd_url: "https://example.serverdensity.io"
sd_api_token: "your_api_key"
sd_group: "{{ tag_class_foo }}" # optional definition of SD group
```

Failure to define the above will likely cause this role to bail out, as there will never be default values set for `sd_url` or `sd_api_token`.

Optional variables: (and their defaults). More info can be found in `roles/infowolfe.sd-agent/templates/config.cfg.j2`

```yaml
---
- sd:
  - loglevel: error
  - plugin_dir: no default 
  - rundir: /run
  - tmpdir: /tmp/sd-agent
  - apache_status_url: ''
  - apache_user: ''
  - apache_pass: ''
  - mongodb_server: ''
  - mongodb_dbstats: ''
  - mongodb_replset: ''
  - mysql_server: ''
  - mysql_user: ''
  - mysql_pass: ''
  - nginx_status_url: ''
  - rabbitmq_status_url: http://localhost:55672/api/overview
  - rabbitmq_user: guest
  - rabbitmq_pass: guest
```

### Dependencies

None.

### Example Playbook

```yaml
- hosts: servers
  roles:
    - { role: infowolfe.sd-agent }
```

### License

BSD

### Author Information

I'm reachable on freenode (#ansible), on twitter, google hangouts (né google talk - jabber) and via issues/pull requests here on [github]. If you're clever, you'll note that I also have an email address on gmail.
