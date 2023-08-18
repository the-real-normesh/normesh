# nmsh-netns

Create and use named network namespaces with Systemd.

## Version

## Unit file templates
**nmsh-netns\@.service**
- create a named network namespace which other Systemd services can bind to

**nmsh-netns-setup\@.service**
- perform setup of a created network namespace

## Usage
```shell
export NAMESPACE=testns
mkdir -p "/etc/nmsh/netns/${NAMESPACE}.d"
echo "IFACES=(eth1 eth2 eth3)" > "/etc/nmsh/netns/${NAMESPACE}.d/interfaces.conf"

# enable the namespace instance
systemctl enable "nmsh-netns@${NAMESPACE}"
# and start it
systemctl start "nmsh-netns@${NAMESPACE}"

# or, do it in one command
systemctl --now enable "nmsh-netns@${NAMESPACE}"

# set up the namespace
# enable the namespace instance
systemctl enable "nmsh-netns-setup@${NAMESPACE}"
# and start it
systemctl start "nmsh-netns-setup@${NAMESPACE}"

# or, do it in one command
systemctl --now enable "nmsh-netns-setup@${NAMESPACE}"
```
