AAA Role for Dell EMC Networking OS
===================================

This role facilitates the configuration of Authentication Authorization Acccounting (AAA). It supports the configuration of TACACS and RADIUS server and AAA. This role is abstracted for dellos9.

Installation
------------

```
ansible-galaxy install Dell-Networking.dellos-aaa
```

Requirements
------------
This role requires an SSH connection for connectivity to your Dell EMC Networking device. You can use any of the built-in OS connection variables or the ``provider`` dictionary.

Role Variables
--------------

This role is abstracted using the ``ansible_net_os_name`` variable that can take the following value "dellos9".

Any role variable with a corresponding state variable set to absent negates the configuration of that variable. For variables with no state variable, setting an empty value for the variable negates the corresponding configuration. The variables and its values are case-sensitive.

``dellos_aaa`` contains the following keys:

|        Key | Type                      | Notes                                                                                                                                                                                     |
|------------|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| radius_server | dictionary        | Configures the radius server. See the following radius_server.* for each item.      |
| radius_server.key | string (required), choices: 0,7,LINE           | Configures the authentication key for radius server. |
| radius_server.key_string | string           | Configures the user key string. If key is 7, this variable takes the hidden user key string. If key is 0, takes the unencrypted user key(clear text). This variable is supported only if the value of radius_server.key is 7 or 0.                            |
| radius_server.retransmit | integer         | Configures the number of retransmissions.                           |
| radius_server.timeout | integer         | Configures timeout for retransmissions.                           |
| radius_server.deadtime | integer         | Configures the server dead time.                           |
| radius_server.group | dictionary         | Configures the group of radius servers. See the following group.* for each item.                           |
| group.name | string(required)         | Configures the group name of the radius servers.                           |
| group.host| dictionary         | Configures the radius server host in the group. See the following host.* for each item.                        |
| host.ip | string         | Configures the radius server host address in the group.                           |
| host.key | string (required), choices: 0,7,LINE           | Configures the authentication key. |
| host.key_string | string           | Configures the user key string. If key is 7, this variable takes the hidden user key string. If key is 0, takes the unencrypted user key(clear text). This variable is supported only if the value of host.key is 7 or 0.                            |
| host.retransmit | integer         | Configures the number of retransmissions.                           |
| host.auth_port | integer         | Configures the authentication port. The value can be in the range 0-65535     |
| host.timeout | Integer         | Configures timeout for retransmissions.                           |
| host.state | string, choices: present,absent         | If set to absent, removes the host from group of radius server.                           |
| group.vrf | dictionary         | Configures VRF for radius servers in the group. See the following vrf.* for each item.                        |
| vrf.vrf_name | string(required)       | Configures the name of vrf for radius server group.                         |
| vrf.source_intf | Integer         | Configures source interface for outgoing packets from servers in the group.      |
| vrf.state | string, choices: present,absent         | If set to absent, removes the VRF from group of radius server.  |
| group.state | string, choices: present,absent         | If set to absent, removes the radius server group.            |
| radius_server.host| dictionary         | Configures the radius server host. See the following host.* for each item. |
| host.ip | string         | Configures the radius server host address.                           |
| host.key | string (required), choices: 0,7,LINE           | Configures the authentication key. |
| host.key_string | string           | Configures the user key string. If key is 7, this variable takes the hidden user key string. If key is 0, takes the unencrypted user key(clear text). This variable is supported only if the value of host.key is 7 or 0.                            |
| host.retransmit | integer         | Configures the number of retransmissions.                           |
| host.auth_port | integer         | Configures the authentication port. The value can be in the range 0-65535     |
| host.timeout | Integer         | Configures timeout for retransmissions.                           |
| host.state | string, choices: present,absent         | If set to absent, removes the radius server host.           |
| tacacs_server | dictionary        | Configures the tacacs server. See the following tacacs_server.* for each item.      |
| tacacs_server.key | string (required), choices: 0,7,LINE           | Configures the authentication key for tacacs server. |
| tacacs_server.key_string | string           | Configures the user key string. If key is 7, this variable takes the hidden user key string. If key is 0, takes the unencrypted user key(clear text). This variable is supported only if the value of tacacs_server.key is 7 or 0.                          |
| tacacs_server.group | dictionary         | Configures the group of tacacs servers. See the following group.* for each item.                           |
| group.name | string(required)         | Configures the group name of the tacacs servers.                           |
| group.host| dictionary         | Configures the tacacs server host in the group. See the following host.* for each item.                        |
| host.ip | string         | Configures the tacacs server host address in the group.                           |
| host.key | string (required), choices: 0,7,LINE           | Configures the authentication key of tacacs server host. |
| host.key_string | string           | Configures the user key string. If key is 7, this variable takes the hidden user key string. If key is 0, takes the unencrypted user key(clear text). This variable is supported only if the value of host.key is 7 or 0.                            |
| host.retransmit | integer         | Configures the number of retransmissions.                           |
| host.auth_port | integer         | Configures the authentication port. The value can be in the range 0-65535     |
| host.timeout | Integer         | Configures timeout for retransmissions.                           |
| host.state | string, choices: present,absent         | If set to absent, removes the host from group of tacacs server.                           |
| group.vrf | dictionary         | Configures VRF for tacacs servers in the group. See the following vrf.* for each item.                        |
| vrf.vrf_name | string(required)       | Configures the name of vrf for tacacs server group.                         |
| vrf.source_intf | integer         | Configures source interface for outgoing packets from servers in the group.      |
| vrf.state | string, choices: present,absent         | If set to absent, removes the VRF from group of tacacs server.  |
| group.state | string, choices: present,absent         | If set to absent, removes the tacacs server group.            |
| tacacs_server.host| dictionary         | Configures the tacacs server host. See the following host.* for each item. |
| host.ip | string         | Configures the tacacs sever host address.                           |
| host.key | string (required), choices: 0,7,LINE           | Configures the authentication key. |
| host.key_string | string           | Configures the user key string. If key is 7, this variable takes the hidden user key string. If key is 0, takes the unencrypted user key(clear text). This variable is supported only if the value of host.key is 7 or 0.                            |
| host.retransmit | integer         | Configures the number of retransmissions.                           |
| host.auth_port | integer         | Configures the authentication port. The value can be in the range 0-65535     |
| host.timeout | Integer         | Configures timeout for retransmissions.                           |
| host.state | string, choices: present,absent         | If set to absent, removes the tacacs server host.           |
| aaa_accounting | dictionary        | Configures accounting parameters. See the following aaa_accounting.* for each item.     |
| aaa_accounting.commands | list        | Configures accounting for exec(shell) and config commands. See the following commands.* for each item.      |
| commands.enable_level | integer         | Configures enable level for accounting of commands.                |
| commands.role_name | string         | Configures user role for accounting of commands. This variable is mutually exclusive with enable_level.                |
| commands.accounting_list_name | integer         | Configures named accounting list for commands.                |
| commands.no_accounting | boolean        | Configures no accounting of commands.|
| commands.record_option | string, choices: start-stop,stop-only,wait-start        | Configures options to record data.             |
| commands.state | string, choices: present,absent         | If set to absent, removes the named accounting list for the commands.           |
| aaa_accounting.exec | list        | Configures accounting for exec(shell) commands. See the following exec.* for each item.      |
| exec.accounting_list_name | string         | Configures named accounting list for exec commands.                |
| exec.no_accounting | boolean         | Configures no accounting of exec commands.|
| exec.record_option | string, choices: start-stop,stop-only,wait-start      | Configures options to record data.       |
| exec.state | string, choices: present,absent         | If set to absent, removes the named accounting list for the exec commands.           |
| aaa_accounting.suppress | boolean        | Suppresses accounting for users with NULL username      |
| aaa_accounting.dot1x | string, choices: none,start-stop,stop-only,wait-start        | Configures accounting for dot1x events.      |
| aaa_accounting.rest | string, choices: none,start-stop,stop-only,wait-start        | Configures accounting for rest interface events.      |
| aaa_authorization | dictionary        | Configures authorization parameters. See the following aaa_authorization.* for each item.      |
| aaa_authorization.commands | list        | Configures authorization for exec(shell) and config commands. See the following commands.* for each item.      |
| commands.enable_level | integer         | Configures enable level for authorization of commands.                |
| commands.role_name | string         | Configures user role for authorization of commands. This variable is mutually exclusive with enable_level.                |
| commands.authorization_list_name | string         | Configures named authorization list for commands.                |
| commands.authorization_methiod | string, choices: none         | Configures no authorization of commands.|
| commands.use_data | string, choices: local,tacacs+        | Configures data used for authorization.                |
| commands.state | string, choices: present,absent         | If set to absent, removes the named authorization list for the commands.           | 
| aaa_authorization.config_commands | boolean        | Configures authorization for configuration mode commands.      |
| aaa_authorization.role_only | boolean        | Configures validation of authentication mode for user role.      |
| aaa_authorization.exec | list        | Configures authorization for exec(shell) commands. See the following exec.* for each item.      |
| exec.authorization_list_name | string         | Configures named authorization list for exec commands.                |
| exec.authorization_methiod | string, choices: none         | Configures no authorization of exec commands.|
| exec.use_data | string, choices: local,tacacs+        | Configures data used for authorization.                |
| exec.state | string, choices: present,absent         | If set to absent, removes the named authorization list for the exec commands.           |
| aaa_authentication | dictionary        | Configures authentication parameters. See the following aaa_authentication.* for each item.      |
| aaa_radius | dictionary        | Configures AAA for radius group of servers. See the following aaa_radius.* for each item.     |
| aaa_radius.group | string        | Configures name of the radius group of servers for AAA.      |
| aaa_radius.auth_method | string, choices: pap,mschapv2    | Configures authentication method of radius group of servers for AAA.      |
| aaa_tacacs | dictionary | Configures AAA for tacacs group of servers. See the following aaa_tacacs.* for each item.     |
| aaa_tacacs.group | string        | Configures name of the tacacs group of servers for AAA.      |
| aaa_authentication.auth_list | list        | Configures named authentication list for hosts. See the following host.* for each item.      |
| auth_list.name | string         | Configures named authentication list.                |
| auth_list.login_or_enable | string, choices: enable,login         | Configures authentication list for login or enable.     |
| auth_list.server | string, choices: radius,tacacs+         | Configures AAA to use this list of all server hosts.     |
| auth_list.use_password | string, choices: line,local,enable,none         | Configures password to use for authentication. |
| auth_list.state | string, choices: present,absent         | If set to absent, removes the named authentication list.       |
| line_terminal | dictionary | Configures the terminal line. See the following line_terminal.* for each item. |
| line_terminal.&lt;terminal&gt; | dictionary | Configures the primary or virtual terminal line. The value can be of following: console &lt;line_number&gt; , vty &lt;line_number&gt;. See the following &lt;terminal&gt;.* for each item. |
| &lt;terminal&gt;.authorization | dictionary | Configures authorization parameters of line terminal. See the following authorization.* for each item. |
| authorization.commands | list        | Configures authorization for exec(shell) and config commands. See the following commands.* for each item.      |
| commands.enable_level | integer         | Configures enable level for authorization of commands at line terminal.                |
| commands.role_name | string         | Configures user role for authorization of commands at line terminal. This variable is mutually exclusive with enable_level.                |
| commands.authorization_list_name | string         | Configures named authorization list for commands.                |
| commands.state | string, choices: present,absent         | If set to absent, removes the authorization of commands from line terminal.           |
| authorization.exec | list        | Configures authorization for exec(shell) commands at line terminal. See the following exec.* for each item.      |
| exec.authorization_list_name | string         | Configures named authorization list for exec commands.           |
| exec.state | string, choices: present,absent         | If set to absent, removes the authorization of exec(shell) from line terminal.           |
| &lt;terminal&gt;.accounting | dictionary | Configures accounting parameters of line terminal. See the following accounting.* for each item. |
| accounting.commands | list        | Configures accounting for exec(shell) and config commands. See the following commands.* for each item.      |
| commands.enable_level | integer         | Configures enable level for accounting of commands at line terminal.    |
| commands.role_name | string         | Configures user role for accounting of commands at line terminal. This variable is mutually exclusive with enable_level.                |
| commands.accounting_list_name | string         | Configures named accounting list for commands.                |
| commands.state | string, choices: present,absent         | If set to absent, removes the accounting of commands from line terminal.           |
| accounting.exec | list        | Configures accounting for exec(shell) commands at line terminal. See the following exec.* for each item.      |
| exec.accounting_list_name | string         | Configures named accounting list for exec commands.           |
| exec.state | string, choices: present,absent         | If set to absent, removes the accounting of exec(shell) from line terminal.           |
| &lt;terminal&gt;.authentication | dictionary | Configures authentication parameters of line terminal. See the following authentication.* for each item. |
| authentication.enable | string         | Configures the authentication list for previliged level password authentication.    |
| authentication.login | string         | Configures the authentication list for password checking.    |

```
Note: Asterisk (*) denotes the default value if none is specified.
```

Connection Variables
--------------------

Ansible Dell EMC Networking roles require the following connection information to establish communication with the nodes in your inventory. This information can exist in the Ansible group_vars or host_vars directories, or in the playbook itself.


|         Key | Required | Choices    | Description                              |
| ----------: | -------- | ---------- | ---------------------------------------- |
|        host | yes      |            | Hostname or address for connecting to the remote device over the specified ``transport`` variable. The value of this key is the destination address for the transport. |
|        port | no       |            | Port used to build the connection to the remote device. If the value of this key is unspecified, the value defaults to 22. |
|    username | no       |            | Configures the username that authenticates the connection to the remote device. The value of this key authenticates the CLI login. If this key does not specify a value, the value of environment variable ANSIBLE_NET_USERNAME is used instead. |
|    password | no       |            | Specifies the password that authenticates the connection to the remote device. If this key does not specify a value, the value of environment variable ANSIBLE_NET_PASSWORD is used instead. |
|   authorize | no       | yes, no*   | Instructs the module to enter privileged mode on the remote device before sending any commands. If this key does not specify a value, the value of environment variable ANSIBLE_NET_AUTHORIZE is used instead. If not specified, the device attempts to execute all commands in non-privileged mode.|
|   auth_pass | no       |            | Specifies the password to use if required to enter privileged mode on the remote device. If ``authorize`` is set to no, then this key is not applicable. If this key does not specify a value, the value of environment variable ANSIBLE_NET_AUTH_PASS is used instead. |
|   transport | yes      | cli*       | Configures the transport connection to use when connecting to the remote device. This key supports connectivity to the device over CLI (SSH).  |
|    provider | no       |            | Convenient method that passes all of the above connection arguments as a dictionary object. All constraints (such as required or choices) must be met either by individual arguments or values in this dictionary. |


```
Note: Asterisk (*) denotes the default value if none is specified.
```
Dependencies
------------

The dellos-aaa role is built on modules included in the core Ansible code. These modules were added in Ansible version 2.2.0.


Example Playbook
----------------

The following example uses the dellos-aaa role to configure AAA for radius and tacacs servers. The example creates a ``hosts`` file with the switch details and corresponding variables. The hosts file should define the variable `` ansible_net_os_name `` with corresponding Dell EMC networking OS name. It writes a simple playbook that only references the dellos-aaa role.

Sample ``hosts`` file:

    leaf1 ansible_host= <ip_address> ansible_net_os_name= <OS name(dellos9)>

Sample ``host_vars/leaf1``:

    hostname: leaf1
    provider:
      host: "{{ hostname }}"
      username: xxxxx
      password: xxxxx
      authorize: yes
      auth_pass: xxxxx
      transport: cli
    dellos_aaa:
      radius_server:
          key: radius
          retransmit: 5
          timeout: 40
          deadtime: 2300
          group:
            - name: RADIUS
              host:
                - ip: 2001:4898:f0:f09b::1002
                  key: 0
                  key_string: aaaa
                  retransmit: 5
                  auth_port: 3
                  timeout: 2
                  state: present
              vrf:
                vrf_name: test
                source_intf: fortyGigE 1/2
                state: absent
              state: present
          host:
            - ip: 2001:4898:f0:f09b::1002
              key: xxx
              retransmit: 5
              auth_port: 3
              timeout: 2
              state: present
      tacacs_server:
          key: 7
          key_string: 9ea8ec421c2e2e5bec757f44205015f6d81e83a4f0aa52fa
          group:
            - name: TACACS
              host:
                - ip: 2001:4898:f0:f09b::1000
                  key: 0
                  key_string: aaa
                  retransmit: 6
                  auth_port: 3
                  timeout: 2
                  state: present
              vrf:
                vrf_name: tes
                source_intf: fortyGigE 1/3
                state: present
              state: present
          host:
            - ip: 2001:4898:f0:f09b::1000
              key: 0
              key_string: aa
              retransmit: 5
              auth_port: 3
              timeout: 2
              state: present
      aaa_accounting:
          commands:
              - enable_level: 2
                accounting_list_name: aa
                record_option: start-stop
                state: present
              - role_name: netadmin
                accounting_list_name: aa
                no_accounting: none
          suppress: True
          exec:
              - accounting_list_name: aaa
                no_accounting: true
                state: present
          dot1x: none
          rest: none
      aaa_authorization:
          commands:
              - enable_level: 2
                authorization_list_name: aa
                use_data: local
                state: present
              - role_name: netadmin
                authorization_list_name: aa
                authorization_method: none
                use_data: local
          config_commands: True
          role_only:
          exec:
              - authorization_list_name: aaa
                authorization_method: if-authenticated
                use_data: local
                state: present
      aaa_authentication:
          auth_list:
            - name: default
              login_or_enable: login
              server: radius
              use_password: local
              state: present
            - name: console
              server: tacacs+
              login_or_enable: login
              use_password: local
      aaa_radius:
          group: RADIUS
          auth_method: pap
      aaa_tacacs:
          group: TACACS
      line_terminal:
        vty 0:
          authorization:
            commands:
               - enable_level: 2
                 authorization_list_name: aa
                 state: present
               - role_name: netadmin
                 authorization_list_name: aa
                 state: present
            exec:
               - authorization_list_name: aa
                 state: present
          accounting:
            commands:
               - enable_level: 2
                 accounting_list_name: aa
                 state: present
               - role_name: netadmin
                 accounting_list_name: aa
                 state: absent
            exec:
               accounting_list_name: aa
               state: present
          authentication:
            enable:
            login: console


Simple playbook to setup system, ``leaf.yaml``:

    - hosts: leaf1
      roles:
         - Dell-Networking.dellos-aaa

Then run with:

    ansible-playbook -i hosts leaf.yaml

License
-------

Copyright (c) 2017, Dell Inc. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

