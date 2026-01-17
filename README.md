[![Actions Status - Main](https://github.com/juju4/ansible-xrdp/workflows/AnsibleCI/badge.svg)](https://github.com/juju4/ansible-xrdp/actions?query=branch%3Amain)
[![Actions Status - Devel](https://github.com/juju4/ansible-xrdp/workflows/AnsibleCI/badge.svg?branch=devel)](https://github.com/juju4/ansible-xrdp/actions?query=branch%3Adevel)

# xrdp ansible role

Set up [Xrdp](http://xrdp.org/), free and open-source implementation of Microsoft RDP server

## Requirements & Dependencies

### Ansible
It was tested on the following versions:
 * 2.10

### Operating systems

Tested on Ubuntu 18.04, 20.04, Centos 7 and 8.

## Example Playbook

Just include this role in your list.
For example

```
- host: myhost
  roles:
    - juju4.xrdp
```

you probably want to review variables

## Variables

```
xrdp_startwm: 'lxde'
# xrdp_startwm: 'xfce'
# xrdp_startwm: 'gnome'
# xrdp_startwm: 'exec /bin/sh /etc/X11/Xsession'  # whatever custom value

xrdp_enablesyslog: false
```

## Continuous integration

This role has a molecule test suite and github action workflow.

```
$ pip install molecule docker
$ molecule test
$ MOLECULE_DISTRO=ubuntu:20.04 molecule test --destroy=never
```

## Troubleshooting & Known issues

* xrdp requires a complex password (3 of lower, upper, number, special characters) else you may get login failed error. if error persist, try redefining user password just to be sure.

* xrdp can use X11, VNC or other interfaces. Those must be present and working.

* it is recommended to adapt your window manager to your network bandwidth, eg prefer lxde if low bandwidth.

* Misc references
  * https://askubuntu.com/questions/773626/xrdp-login-failed
  * https://github.com/neutrinolabs/xrdp/issues/1061
  * https://linoxide.com/xrdp-connect-ubuntu-linux-remote-desktop-via-rdp-from-windows/
  * https://peteris.rocks/blog/remote-desktop-and-vnc-on-ubuntu-server/

* on xrdp speed, see
https://github.com/neutrinolabs/xrdp/issues/386
https://github.com/neutrinolabs/xrdp/issues/501
https://askubuntu.com/questions/1323601/xrdp-is-quite-slow

* RHEL 10 has removed xrdp package and is not supported

* Debian Trixie (and likely next Ubuntu) has changed local policy rules syntax. See [Polkitd (Policy Kit Daemon) in Trixie ... getting rid of "Authentication is required to create a color profile", May 2025](https://daniel-lange.com/archives/193-Polkitd-Policy-Kit-Daemon-in-Trixie-...-getting-rid-of-Authentication-is-required-to-create-a-color-profile.html)

## License

BSD 2-clause
