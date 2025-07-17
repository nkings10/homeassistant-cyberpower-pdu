# homeassistant-cyberpower-pdu
Instructions to setup a CyberPower PDU41005 PDU in Home Assistant using SNMP

The PDU's credentials are stored in the secrets.yaml file, in configuration.yaml the snmp authentication is in a block and referenced in each sensor and switch.

Edit:
```
nano /mnt/system/appdata/homeassistant/secrets.yaml
```

Add:
```
office_pdu_host: "<your-ip-address>"
office_pdu_username: "<your-username>"
office_pdu_auth_key: "<your-authentication-key>"
office_pdu_priv_key: "<your-private-key>"
```

Edit:
```
nano /mnt/system/appdata/homeassistant/configuration.yaml
```

Add:
```
snmp_auth: &snmp_auth_settings

  host: !secret office_pdu_host
  version: "3"
  username: !secret office_pdu_username
  auth_key: !secret office_pdu_auth_key
  priv_key: !secret office_pdu_priv_key
  auth_protocol: "hmac-sha"
  priv_protocol: "aes-cfb-128"

sensor:

  # Office Desk PDU Voltage
  - platform: snmp
    name: "Office Desk PDU Voltage"
    <<: *snmp_auth_settings
    value_template: "{{ (value | int) / 10 }}" # 2392 / 10 = 239.2 V
    unit_of_measurement: "V"
    baseoid: "1.3.6.1.4.1.3808.1.1.3.2.3.1.1.6.1"

  # Office Desk PDU Active Power
  - platform: snmp
    name: "Office Desk PDU Active Power"
    <<: *snmp_auth_settings
    unit_of_measurement: "W"
    baseoid: "1.3.6.1.4.1.3808.1.1.3.2.3.1.1.7.1"

  # Office Desk PDU Apparent Power
  - platform: snmp
    name: "Office Desk PDU Apparent Power"
    <<: *snmp_auth_settings
    unit_of_measurement: "W"
    baseoid: "1.3.6.1.4.1.3808.1.1.3.2.3.1.1.8.1"

  # Office Desk PDU Power Factor
  - platform: snmp
    name: "Office Desk PDU Power Factor"
    <<: *snmp_auth_settings
    value_template: "{{ (value | int) / 100 }}" # 70 / 100 = 0.7
    baseoid: "1.3.6.1.4.1.3808.1.1.3.2.3.1.1.9.1"

switch:

  # Office Desk PDU Switch 1
  - platform: snmp
    name: "Office Desk PDU Switch 1"
    <<: *snmp_auth_settings
    baseoid: "1.3.6.1.4.1.3808.1.1.3.3.5.1.1.4.1"
    command_oid: "1.3.6.1.4.1.3808.1.1.3.3.3.1.1.4.1"
    payload_on: "1"
    payload_off: "2"

  # Office Desk PDU Switch 2
  - platform: snmp
    name: "Office Desk PDU Switch 2"
    <<: *snmp_auth_settings
    baseoid: "1.3.6.1.4.1.3808.1.1.3.3.5.1.1.4.2"
    command_oid: "1.3.6.1.4.1.3808.1.1.3.3.3.1.1.4.2"
    payload_on: "1"
    payload_off: "2"

  # Office Desk PDU Switch 3
  - platform: snmp
    name: "Office Desk PDU Switch 3"
    <<: *snmp_auth_settings
    baseoid: "1.3.6.1.4.1.3808.1.1.3.3.5.1.1.4.3"
    command_oid: "1.3.6.1.4.1.3808.1.1.3.3.3.1.1.4.3"
    payload_on: "1"
    payload_off: "2"

  # Office Desk PDU Switch 4
  - platform: snmp
    name: "Office Desk PDU Switch 4"
    <<: *snmp_auth_settings
    baseoid: "1.3.6.1.4.1.3808.1.1.3.3.5.1.1.4.4"
    command_oid: "1.3.6.1.4.1.3808.1.1.3.3.3.1.1.4.4"
    payload_on: "1"
    payload_off: "2"

  # Office Desk PDU Switch 5
  - platform: snmp
    name: "Office Desk PDU Switch 5"
    <<: *snmp_auth_settings
    baseoid: "1.3.6.1.4.1.3808.1.1.3.3.5.1.1.4.5"
    command_oid: "1.3.6.1.4.1.3808.1.1.3.3.3.1.1.4.5"
    payload_on: "1"
    payload_off: "2"

  # Office Desk PDU Switch 6
  - platform: snmp
    name: "Office Desk PDU Switch 6"
    <<: *snmp_auth_settings
    baseoid: "1.3.6.1.4.1.3808.1.1.3.3.5.1.1.4.6"
    command_oid: "1.3.6.1.4.1.3808.1.1.3.3.3.1.1.4.6"
    payload_on: "1"
    payload_off: "2"

  # Office Desk PDU Switch 7
  - platform: snmp
    name: "Office Desk PDU Switch 7"
    <<: *snmp_auth_settings
    baseoid: "1.3.6.1.4.1.3808.1.1.3.3.5.1.1.4.7"
    command_oid: "1.3.6.1.4.1.3808.1.1.3.3.3.1.1.4.7"
    payload_on: "1"
    payload_off: "2"

  # Office Desk PDU Switch 8
  - platform: snmp
    name: "Office Desk PDU Switch 8"
    <<: *snmp_auth_settings
    baseoid: "1.3.6.1.4.1.3808.1.1.3.3.5.1.1.4.8"
    command_oid: "1.3.6.1.4.1.3808.1.1.3.3.3.1.1.4.8"
    payload_on: "1"
    payload_off: "2"
```
