ansible-role-openwrt-wpa3
=========================

[![Ansible Role: bit_kitchen.openwrt_wpa3](https://img.shields.io/ansible/role/49499.svg)](https://galaxy.ansible.com/bit_kitchen/openwrt_wpa3)
[![Build Status: bit-kitchen/ansible-role-openwrt-wpa3](https://travis-ci.org/bit-kitchen/ansible-role-openwrt-wpa3.svg?branch=master)](https://travis-ci.org/bit-kitchen/ansible-role-openwrt-wpa3)

```sh
ansible-galaxy install bit_kitchen.openwrt_wpa3
```

This ansible role configures OpenWrt (>= 19.07) for WPA3 support. It installs either `wpad-openssl` (default) or `wpad-wolfssl` to provide WPA3 support as AP (access point) and station (client). For more information, check [OpenWrt Doc](https://openwrt.org/docs/guide-user/network/wifi/basic#WPA%20Modes).

The following conflicting packages will be removed first if installed:

*   hostapd
*   hostapd-basic
*   hostapd-mini
*   wpad
*   wpad-basic
*   wpad-mini

The following conflicting packges won't get removed if installed as they provide WPA3 functionality as well, and this role will fail itself.

*   hostapd-openssl
*   hostapd-wolfssl
*   wpad-mesh-openssl
*   wpad-mesh-wolfssl
*   wpad-openssl
*   wpad-wolfssl

A reboot is required for changes to take effect.

Requirements
------------

*   OpenWrt >= 19.07

Role Variables
--------------

Variable    | Default   | Comment
----------- | --------- | -------
openwrt_ssl | `openssl` | SSL library to use. Options are `openssl` and `wolfssl`.

Dependencies
------------

* `gekmihesg.openwrt`

Example Playbook
----------------

```yml
- name: Configure WPA3 with wpad-openssl
  hosts: openwrt
  remote_user: root
  gather_facts: yes
  roles:
  - bit_kitchen.openwrt_wpa3
```

```yml
- name: Configure WPA3 with wpad-wolfssl
  hosts: openwrt
  remote_user: root
  gather_facts: yes
  roles:
  - name: bit_kitchen.openwrt_wpa3
    openwrt_ssl: wolfssl
```

License
-------

[MIT](LICENSE)

Author Information
------------------

[bit.kitchen](https://github.com/bit-kitchen)
