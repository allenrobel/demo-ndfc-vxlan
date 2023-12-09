# group_vars

Contains vars required by ndfc_* roles

### Requirements

json_query (``pip install jmespath``)

### 01_fabrics.yml

#### VXLAN/EVPN Fabrics (aka EasyFabric)

A dictionary of dictionaries.  Some of the more frequently-used variables are:


Variable              | Example       | Type        | Description
----------------------|---------------|-------------|-------------------
FABRIC_NAME           | f1      | string      | Fabric name
BGP_AS                | 65001         | string      | Fabric BGP autonomous system number
ANYCAST_RP_IP_RANGE   | 10.254.1.0/24 | net/prefix  | Fabric PIM RP. Set only if REPLICATION_MODE == Multicast
LOOPBACK0_IP_RANGE    | 10.2.0.0/22   | net/prefix  | Loopback for routing protocols (OSPF/BGP)
LOOPBACK1_IP_RANGE    | 10.3.0.0/22   | net/prefix  | Loopback for VTEP, associated with nve1 interface
SUBNET_RANGE          | 10.4.0.0/16   | net/prefix  | Inter-device links e.g. spine-leaf
FABRIC_MTU            | 1500          | integer     | Packet Maximum Transfer Unit within the fabric
REPLICATION_MODE      | Multicast     | string      | Replication mode of the fabric. Multicast or Ingress.
ENABLE_PVLAN          | false         | boolean     | Mandatory. enable/disable PVLAN

NOTE: variables below (mis)spelled DEAFULT_* e.g. DEAFULT_QUEUING_POLICY_CLOUDSCALE,
are correct (i.e. NDFC expects these to be spelled incorrectly).  A bug to fix these
was filed, but was Closed with no action taken.

##### Example

```yaml
vxlan_fabric:
    f1:
        FABRIC_NAME: f1
        BGP_AS: 65001
        SITE_ID: 65001
        OSPF_AREA_ID: 0.0.0.0
        L2_SEGMENT_ID_RANGE: 30000-49000
        L3_PARTITION_ID_RANGE: 50000-59000
        NETWORK_VLAN_RANGE: 2300-2999
        VRF_VLAN_RANGE: 2000-2299
        SUBINTERFACE_RANGE: 2-511
        LOOPBACK0_IP_RANGE: 10.10.0.0/22
        LOOPBACK1_IP_RANGE: 10.11.0.0/22
        SUBNET_RANGE: 10.12.0.0/16
        LOOPBACK0_IPV6_RANGE: ""
        LOOPBACK1_IPV6_RANGE: ""
        V6_SUBNET_RANGE: ""
        SUBNET_TARGET_MASK: 30
        DCI_SUBNET_RANGE: 10.13.0.0/16
        DCI_SUBNET_TARGET_MASK: 30
        SERVICE_NETWORK_VLAN_RANGE: 3000-3199
        ROUTE_MAP_SEQUENCE_NUMBER_RANGE: 1-65534
        FABRIC_MTU: 9216
        L2_HOST_INTF_MTU: 9216
        REPLICATION_MODE: Ingress
        ANYCAST_GW_MAC: 2020.0000.00aa
        CDP_ENABLE: false
        ENABLE_EVPN: true
        ENABLE_NGOAM: true
        ENABLE_TENANT_DHCP: true
        ENABLE_MACSEC: false
        ENABLE_NXAPI: true
        ENABLE_PBR: false
        PM_ENABLE: false
        ENABLE_PVLAN: false
        ENABLE_NETFLOW: false
        ENABLE_VPC_PEER_LINK_NATIVE_VLAN: false
        ENABLE_NXAPI_HTTP: true
        ENABLE_TRM: false
        BOOTSTRAP_ENABLE: false
        BFD_ENABLE: false
        BFD_IBGP_ENABLE: false
        BFD_OSPF_ENABLE: false
        BFD_ISIS_ENABLE: false
        BFD_PIM_ENABLE: false
        BFD_AUTH_ENABLE: false
        DHCP_ENABLE: false
        DHCP_IPV6_ENABLE: ""
        DHCP_START: ""
        DHCP_END: ""
        UNDERLAY_IS_V6: false
        USE_LINK_LOCAL: false
        V6_SUBNET_TARGET_MASK: ""
        LINK_STATE_ROUTING: ospf
        VPC_DELAY_RESTORE_TIME: 60
        RR_COUNT: 2
        BGP_AS_PREV: ""
        PM_ENABLE_PREV: false
        ENABLE_FABRIC_VPC_DOMAIN_ID_PREV: ""
        FABRIC_VPC_DOMAIN_ID_PREV: ""
        LINK_STATE_ROUTING_TAG_PREV: ""
        OVERLAY_MODE_PREV: ""
        ENABLE_PVLAN_PREV: ""
        FABRIC_MTU_PREV: 9216
        L2_HOST_INTF_MTU_PREV: 9216
        DEPLOYMENT_FREEZE: false
        INBAND_MGMT_PREV: false
        BOOTSTRAP_ENABLE_PREV: false
        MGMT_V6PREFIX: 64
        ENABLE_NETFLOW_PREV: ""
        FABRIC_TYPE: Switch_Fabric
        ENABLE_AGENT: false
        AGENT_INTF: eth0
        SSPINE_ADD_DEL_DEBUG_FLAG: Disable
        BRFIELD_DEBUG_FLAG: Disable
        ACTIVE_MIGRATION: false
        FF: Easy_Fabric
        MSO_SITE_ID: ""
        MSO_CONTROLER_ID: ""
        MSO_SITE_GROUP_NAME: ""
        PREMSO_PARENT_FABRIC: ""
        MSO_CONNECTIVITY_DEPLOYED: ""
        ANYCAST_RP_IP_RANGE_INTERNAL: ""
        DHCP_START_INTERNAL: ""
        DHCP_END_INTERNAL: ""
        DHCP_IPV6_ENABLE_INTERNAL: ""
        MGMT_GW_INTERNAL: ""
        MGMT_PREFIX_INTERNAL: ""
        BOOTSTRAP_MULTISUBNET_INTERNAL: ""
        MGMT_V6PREFIX_INTERNAL: ""
        UNNUM_DHCP_START_INTERNAL: ""
        UNNUM_DHCP_END_INTERNAL: ""
        FEATURE_PTP_INTERNAL: false
        SSPINE_COUNT: 0
        SPINE_COUNT: 0
        abstract_feature_leaf: base_feature_leaf_upg
        abstract_feature_spine: base_feature_spine_upg
        abstract_dhcp: base_dhcp
        abstract_multicast: base_multicast_11_1
        abstract_anycast_rp: anycast_rp
        abstract_loopback_interface: int_fabric_loopback_11_1
        abstract_isis: base_isis_level2
        abstract_ospf: base_ospf
        abstract_vpc_domain: base_vpc_domain_11_1
        abstract_vlan_interface: int_fabric_vlan_11_1
        abstract_isis_interface: isis_interface
        abstract_ospf_interface: ospf_interface_11_1
        abstract_pim_interface: pim_interface
        abstract_route_map: route_map
        abstract_bgp: base_bgp
        abstract_bgp_rr: evpn_bgp_rr
        abstract_bgp_neighbor: evpn_bgp_rr_neighbor
        abstract_extra_config_leaf: extra_config_leaf
        abstract_extra_config_spine: extra_config_spine
        abstract_extra_config_tor: extra_config_tor
        abstract_extra_config_bootstrap: extra_config_bootstrap_11_1
        temp_anycast_gateway: anycast_gateway
        temp_vpc_domain_mgmt: vpc_domain_mgmt
        temp_vpc_peer_link: int_vpc_peer_link_po
        abstract_routed_host: int_routed_host
        abstract_trunk_host: int_trunk_host
        L3VNI_MCAST_GROUP: ""
        PHANTOM_RP_LB_ID1: ""
        PHANTOM_RP_LB_ID2: ""
        PHANTOM_RP_LB_ID3: ""
        PHANTOM_RP_LB_ID4: ""
        VPC_PEER_LINK_VLAN: 3600
        VPC_PEER_KEEP_ALIVE_OPTION: management
        VPC_AUTO_RECOVERY_TIME: 360
        VPC_DELAY_RESTORE: 150
        VPC_PEER_LINK_PO: 500
        VPC_ENABLE_IPv6_ND_SYNC: true
        ADVERTISE_PIP_BGP: false
        ENABLE_FABRIC_VPC_DOMAIN_ID: false
        FABRIC_VPC_DOMAIN_ID: ""
        FABRIC_VPC_QOS_POLICY_NAME: ""
        BGP_LB_ID: 0
        NVE_LB_ID: 1
        ANYCAST_LB_ID: ""
        LINK_STATE_ROUTING_TAG: UNDERLAY
        OSPF_AUTH_KEY_ID: ""
        OSPF_AUTH_KEY: ""
        ISIS_LEVEL: ""
        ISIS_P2P_ENABLE: false
        ISIS_AUTH_ENABLE: false
        ISIS_AUTH_KEYCHAIN_NAME: ""
        ISIS_AUTH_KEYCHAIN_KEY_ID: ""
        ISIS_AUTH_KEY: ""
        ISIS_OVERLOAD_ENABLE: false
        ISIS_OVERLOAD_ELAPSE_TIME: ""
        BGP_AUTH_KEY_TYPE: ""
        BGP_AUTH_KEY: ""
        PIM_HELLO_AUTH_KEY: ""
        BFD_AUTH_KEY_ID: ""
        BFD_AUTH_KEY: ""
        IBGP_PEER_TEMPLATE: ""
        IBGP_PEER_TEMPLATE_LEAF: ""
        default_vrf: Default_VRF_Universal
        default_network: Default_Network_Universal
        vrf_extension_template: Default_VRF_Extension_Universal
        network_extension_template: Default_Network_Extension_Universal
        OVERLAY_MODE: config-profile
        default_pvlan_sec_network: ""
        HOST_INTF_ADMIN_STATE: true
        POWER_REDUNDANCY_MODE: ps-redundant
        COPP_POLICY: strict
        HD_TIME: 180
        BROWNFIELD_NETWORK_NAME_FORMAT: Auto_Net_VNI$$VNI$$_VLAN$$VLAN_ID$$
        BROWNFIELD_SKIP_OVERLAY_NETWORK_ATTACHMENTS: false
        STRICT_CC_MODE: false
        AAA_REMOTE_IP_ENABLED: false
        SNMP_SERVER_HOST_TRAP: true
        ANYCAST_BGW_ADVERTISE_PIP: false
        PTP_LB_ID: ""
        PTP_DOMAIN_ID: ""
        MPLS_LB_ID: ""
        TCAM_ALLOCATION: true
        DEAFULT_QUEUING_POLICY_CLOUDSCALE: ""
        DEAFULT_QUEUING_POLICY_R_SERIES: ""
        DEAFULT_QUEUING_POLICY_OTHER: ""
        MACSEC_KEY_STRING: ""
        MACSEC_ALGORITHM: ""
        MACSEC_FALLBACK_KEY_STRING: ""
        MACSEC_FALLBACK_ALGORITHM: ""
        MACSEC_CIPHER_SUITE: ""
        MACSEC_REPORT_TIMER: ""
        STP_ROOT_OPTION: unmanaged
        STP_VLAN_RANGE: ""
        MST_INSTANCE_RANGE: ""
        STP_BRIDGE_PRIORITY: ""
        EXTRA_CONF_LEAF: ""
        EXTRA_CONF_SPINE: ""
        EXTRA_CONF_TOR: ""
        EXTRA_CONF_INTRA_LINKS: ""
        STATIC_UNDERLAY_IP_ALLOC: false
        MPLS_LOOPBACK_IP_RANGE: ""
        ROUTER_ID_RANGE: ""
        VRF_LITE_AUTOCONFIG: Manual
        AUTO_SYMMETRIC_VRF_LITE: false
        AUTO_VRFLITE_IFC_DEFAULT_VRF: false
        AUTO_SYMMETRIC_DEFAULT_VRF: false
        DEFAULT_VRF_REDIS_BGP_RMAP: ""
        DNS_SERVER_IP_LIST: ""
        DNS_SERVER_VRF: ""
        NTP_SERVER_IP_LIST: ""
        NTP_SERVER_VRF: ""
        SYSLOG_SERVER_IP_LIST: ""
        SYSLOG_SEV: ""
        SYSLOG_SERVER_VRF: ""
        AAA_SERVER_CONF: ""
        MGMT_GW: ""
        MGMT_PREFIX: ""
        BOOTSTRAP_MULTISUBNET: ""
        SEED_SWITCH_CORE_INTERFACES: ""
        SPINE_SWITCH_CORE_INTERFACES: ""
        INBAND_DHCP_SERVERS: ""
        UNNUM_BOOTSTRAP_LB_ID: ""
        UNNUM_DHCP_START: ""
        UNNUM_DHCP_END: ""
        ENABLE_AAA: false
        BOOTSTRAP_CONF: ""
        enableRealTimeBackup: ""
        enableScheduledBackup: ""
        scheduledTime: ""
        NETFLOW_EXPORTER_LIST: ""
        NETFLOW_RECORD_LIST: ""
        NETFLOW_MONITOR_LIST: ""
        FABRIC_INTERFACE_TYPE: p2p
        VPC_DOMAIN_ID_RANGE: 1-1000
        FABRIC_VPC_QOS: false
        OSPF_AUTH_ENABLE: false
        BGP_AUTH_ENABLE: false
        GRFIELD_DEBUG_FLAG: Disable
        FEATURE_PTP: false
        MPLS_HANDOFF: false
        ENABLE_DEFAULT_QUEUING_POLICY: false
        INBAND_MGMT: false
        MULTICAST_GROUP_SUBNET: ""
        RP_COUNT: ""
        RP_MODE: ""
        RP_LB_ID: ""
        PIM_HELLO_AUTH_ENABLE: false
        ANYCAST_RP_IP_RANGE: ""
```

### 02_devices.yml

#### devices
A dictionary of dictionaries
The dictionaries all have the same format.

For purposes of example, an explicit fabric name is given below, but it's recommended that the jinja2 template is used to reference the fabric name in the fabrics dictionary to avoid unnecessary repetition of variable names.

Variable              | Example       | Type       | Description
----------------------|---------------|------------|-------------------
ip                    | 192.168.1.1   | string     | switch mgmt0 ip address
name                  | leaf_1        | string     | switch name
preserve_config       | false         | boolean    | If false, write erase the config during device discovery
role                  | leaf          | string     | The role of the switch.
switch_fabric         | f1      | string     | Fabric in which the switch resides

##### Example

```yaml
devices:
  # lan_classic fabric LC_1
  # preserve_config must be set to True for LAN Classic fabrics
  leaf_1:
    name: leaf_1
    switch_fabric: "{{ vxlan_fabric.f1.name }}"
    ip: 172.22.150.102
    role: leaf
    preserve_config: false
  leaf_2:
    name: leaf_2
    switch_fabric: "{{ vxlan_fabric.f1.name }}"
    ip: 172.22.150.103
    role: leaf
    preserve_config: false
```


### 03_networks.yaml

#### port_groups

Dictionary containing lists of ports to which networks are attached.  These are referenced with the ``networks`` dictionary

##### Example

```yaml
port_groups:
  pg11:
  - Ethernet1/11
  pg12:
  - Ethernet1/12
```

#### networks

Dictionary of dictionaries which define networks and their attachments (device + port_group).

Variable              | Example        | Type         | Description
----------------------|----------------|--------------|-------------------
fabric                | f1             | string       | Fabric in which network resides
net_name              | network_1      | string       | name of the network
vrf_name              | vrf_1          | string       | vrf in which network resides
vlan_id               | 45             | integer      | vlan associated with the network
gw_ip_subnet          | 10.1.1.1/24    | net/prefix   | gateway IP for the network
attach                | See example    | list of dict | List of dictionaries defining the attachment
attach.ip_address     | 192.168.1.1    | IP address   | mgmt0 address of the switch to which the network is attached
attach.ports          | See example    | list         | list of ports on the switch to which the network is attached


##### Example

Below, network n1111 (10.21.1.0/24), with gateway 10.21.1.1, in fabric f1, is connected to four leafs on port port-channel11 on each leaf, within vrf v1.

```yaml
networks:
  f1_n1111:
    name: f1_n1111 # name must be unique across all fabrics
    fabric: "{{ vxlan_fabric.f1.name }}"
    net_name: n1111 # can be the same across fabrics
    vrf_name: v1
    vlan_id: 1111
    gw_ip_subnet: "10.21.1.1/24"
    tag: 12345 # used in service_route_peerings
    attach:
      - ip_address: "{{ devices.leaf_1.ip }}"
        ports: "{{ port_groups.pg11 }}"
      - ip_address: "{{ devices.leaf_2.ip }}"
        ports: "{{ port_groups.pg11 }}"
      - ip_address: "{{ devices.leaf_3.ip }}"
        ports: "{{ port_groups.pg11 }}"
      - ip_address: "{{ devices.leaf_4.ip }}"
        ports: "{{ port_groups.pg11 }}"

  f1_n1112:
    name: f1_n1112
    fabric: "{{ vxlan_fabric.f1.name }}"
    net_name: n1112
    vrf_name: v2
    vlan_id: 1112
    gw_ip_subnet: "10.22.1.1/24"
    tag: 12345
    attach:
      - ip_address: "{{ devices.leaf_1.ip }}"
        ports: "{{ port_groups.pg12 }}"
      - ip_address: "{{ devices.leaf_2.ip }}"
        ports: "{{ port_groups.pg12 }}"
      - ip_address: "{{ devices.leaf_3.ip }}"
        ports: "{{ port_groups.pg12 }}"
      - ip_address: "{{ devices.leaf_4.ip }}"
        ports: "{{ port_groups.pg12 }}"
```

### 04_vrfs.yml

#### vrfs

Dictionary which define VRFs and their attachments (device).
This follows the same property names and (more or less) the general structure as the corresponding Ansible [cisco.dcnm_vrf](https://github.com/CiscoDevNet/ansible-dcnm/blob/main/docs/cisco.dcnm.dcnm_vrf_module.rst) module.

Variable               | Example        | Type         | Description
-----------------------|----------------|--------------|-------------------
fabric                 | f1             | string       | Fabric in which vrf resides
import_vpn_rt          | 65000:50001    | string       | vpn route-target to import
import_evpn_rt         | 65000:50001    | string       | evpn route-target to import
vrf_name               | vrf_1          | string       | name of the vrf
vrf_id                 | 9003031        | integer      | vrf Layer3 VNI / vn-segment
vlan_id                | 3031           | integer      | vrf associated vlan 
vrf_template           | TemplateVrf    | string       | Overlay VRF Template For Leafs
vrf_extension_template | TemplateExVrf  | string       | Overlay VRF Template For Borders
service_vrf_template   | ServiceVrf     | string       | Service vrf template
attach                 | See example    | list of dict | List of mgmt0 ip addresses of switches on which the VRF is configured
attach.ip_address      | 192.168.1.1    | IP address   | mgmt0 address of the switch to which the vrf is attached

##### Example
```yaml
vrfs:
  f1_v1:
    name: f1_v1
    fabric: "{{ vxlan_fabric.f1.name }}"
    vrf_name: v1
    vrf_id: 63031
    vlan_id: 3031
    # You could explicitely list these as well...
    # import_vpn_rt: 65001:63031,65002:63032
    # import_evpn_rt: 65001:63031,65002:63032
    import_vpn_rt: "{{ vxlan_fabric.f1.BGP_AS }}:63031,{{ vxlan_fabric.f2.BGP_AS }}:63032"
    import_evpn_rt: "{{ vxlan_fabric.f1.BGP_AS }}:63031,{{ vxlan_fabric.f2.BGP_AS }}:63032"
    vrf_template: Default_VRF_Universal
    vrf_extension_template: Default_VRF_Extension_Universal
    service_vrf_template: null
    attach:
    - ip_address: "{{ devices.leaf_1.ip }}"
    - ip_address: "{{ devices.leaf_2.ip }}"
    - ip_address: "{{ devices.leaf_3.ip }}"
    - ip_address: "{{ devices.leaf_4.ip }}"

  f1_v2:
    name: f1_v2
    fabric: "{{ vxlan_fabric.f1.name }}"
    vrf_name: v2
    vrf_id: 63032
    vlan_id: 3032
    import_vpn_rt: "{{ vxlan_fabric.f1.BGP_AS }}:63031,{{ vxlan_fabric.f2.BGP_AS }}:63032"
    import_evpn_rt: "{{ vxlan_fabric.f1.BGP_AS }}:63031,{{ vxlan_fabric.f2.BGP_AS }}:63032"
    vrf_template: Default_VRF_Universal
    vrf_extension_template: Default_VRF_Extension_Universal
    service_vrf_template: null
    attach:
    - ip_address: "{{ devices.leaf_1.ip }}"
    - ip_address: "{{ devices.leaf_2.ip }}"
    - ip_address: "{{ devices.leaf_3.ip }}"
    - ip_address: "{{ devices.leaf_4.ip }}"
```


### Licensing

GNU General Public License v3.0 or later.

See [LICENSE](https://www.gnu.org/licenses/gpl-3.0.txt) for full text.

### Author Information

Allen Robel (@packetcalc)
