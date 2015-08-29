# runit services base setup

To be used with other roles to provide runit services to them

## The following variables must be set up to create the service:

runit_service_name | name of the service
runit_service_user | user the service will be running with
runit_service_command | command to start service
runit_service_params | params passed to command
runit_service_kill | process name to kill to resytart the service

## Example:

```
dependencies:
  - { role: runit, runit_service_name: "{{ cassandra_runit }}",  runit_service_user: "{{ cassandra_user }}", runit_service_command: "{{ cassandra_path_install }}/{{ cassandra_start }}", runit_service_params: "", runit_service_kill: "{{ cassandra_kill }}" }
```


