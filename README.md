# runit services base setup

To be used with other roles to provide runit services to them

## The following variables must be set up to create the service:

runit_service_name | name of the service
runit_service_user | user the service will be running with
runit_service_command | command to start service
runit_service_params | params passed to command
runit_allow_user_control | optional, allow service to be controlled by runit_service_user, false by default
runit_service_env | optional, dictionary of environment variables

## Example:

```
dependencies:
  - role: runit
    runit_service_name: "{{ cassandra_runit }}"
    runit_service_user: "{{ cassandra_user }}"
    runit_service_command: "{{ cassandra_path_install }}/{{ cassandra_start }}"
    # optional:
    runit_service_params: ""
    runit_log_transmit_address: 127.0.0.1
    runit_log_transmit_only: no
    runit_log_transmit_port: 514
    runit_log_timeout: "{{ 3600*24 }}"
    runit_log_size: 0
    runit_log_num: 7
    runit_log_min: 3
```

See defaults for some more optional variables and check out svlogd [documentaion](http://smarden.org/runit/svlogd.8.html).
