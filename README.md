<seotitle>NDFC VXLAN/EVPN fabric using Ansible</seotitle>

# ndfc-roles

## Getting started

This repo contains a playbook that uses [ndfc-roles](https://github.com/allenrobel/ndfc-roles) to create a spine-leaf VXLAN/EVPN fabric.

Please read the documentation at the ndfc-roles repo for specifics about how these roles work.

All extraneous roles have been removed to focus on the basics for creating this specific fabric type.

Fabric Specifications

- 3x Leaf
- 2x Spine
- 2x VRF (VRF v1 and v2) present on all Leaf
- One loopback in each VRF is created on each Leaf for use in verifying inter/intra-VRF routing without the need of physical interfaces.

Should you have hosts or traffic generators available, the following are also configured:

- SVIs on each Leaf in each VRF are configured (these have autostate disabled so that they are UP without the underlying physical interfaces being UP).  You can remove this by editing the file inventory/group_vars/ndfc/01_fabrics.yml and removing the configuration from EXTRA_CONF_LEAF i.e. set EXTRA_CONF_LEAF to an empty string:

```yaml
EXTRA_CONF_LEAF: ""
```

- Ethernet1/11 on each Leaf configured as a switchport in vlan 1111 which is associated with VRF v1.
- Ethernet1/12 on each Leaf configured as a switchport in vlan 1112 which is associated with VRF v2.

### Code of Conduct

This repository follows the Contributor Covenant [Code of Conduct](https://github.com/allenrobel/ndfc-roles/blob/master/CODE_OF_CONDUCT.md).

### Licensing

GNU General Public License v3.0 or later.

See [LICENSE](https://www.gnu.org/licenses/gpl-3.0.txt) for full text.
