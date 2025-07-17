# homeassistant-cyberpower-pdu
Instructions to setup a CyberPower PDU41005 PDU in Home Assistant using SNMP

The PDU's credentials are stored in the secrets.yaml file, in configuration.yaml the snmp authentication is in a block and referenced in each sensor and switch.

Scripts are used as the switch instead, as the native SNMP switches dont update instantly. So a script with a 500ms delay before triggering an update is used instead as a work around.

Note: The paths referenced are specific to my Home Assistant container on unRAID, adjust to suit yours.

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
nano /mnt/system/appdata/homeassistant/scripts.yaml
```

Add:
```
# Office Desk PDU Switch 1 On
office_desk_pdu_switch_1_on:
  alias: "Office Desk PDU Switch 1 - On"
  sequence:
    - service: switch.turn_on
      target:
        entity_id: "switch.office_desk_pdu_switch_1"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_1"

# Office Desk PDU Switch 1 Off
office_desk_pdu_switch_1_off:
  alias: "Office Desk PDU Switch 1 - Off"
  sequence:
    - service: switch.turn_off
      target:
        entity_id: "switch.office_desk_pdu_switch_1"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_1"

# Office Desk PDU Switch 2 On
office_desk_pdu_switch_2_on:
  alias: "Office Desk PDU Switch 2 - On"
  sequence:
    - service: switch.turn_on
      target:
        entity_id: "switch.office_desk_pdu_switch_2"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_2"

# Office Desk PDU Switch 2 Off
office_desk_pdu_switch_2_off:
  alias: "Office Desk PDU Switch 2 - Off"
  sequence:
    - service: switch.turn_off
      target:
        entity_id: "switch.office_desk_pdu_switch_2"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_2"

# Office Desk PDU Switch 3 On
office_desk_pdu_switch_3_on:
  alias: "Office Desk PDU Switch 3 - On"
  sequence:
    - service: switch.turn_on
      target:
        entity_id: "switch.office_desk_pdu_switch_3"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_3"

# Office Desk PDU Switch 3 Off
office_desk_pdu_switch_3_off:
  alias: "Office Desk PDU Switch 3 - Off"
  sequence:
    - service: switch.turn_off
      target:
        entity_id: "switch.office_desk_pdu_switch_3"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_3"

# Office Desk PDU Switch 4 On
office_desk_pdu_switch_4_on:
  alias: "Office Desk PDU Switch 4 - On"
  sequence:
    - service: switch.turn_on
      target:
        entity_id: "switch.office_desk_pdu_switch_4"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_4"

# Office Desk PDU Switch 4 Off
office_desk_pdu_switch_4_off:
  alias: "Office Desk PDU Switch 4 - Off"
  sequence:
    - service: switch.turn_off
      target:
        entity_id: "switch.office_desk_pdu_switch_4"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_4"

# Office Desk PDU Switch 5 On
office_desk_pdu_switch_5_on:
  alias: "Office Desk PDU Switch 5 - On"
  sequence:
    - service: switch.turn_on
      target:
        entity_id: "switch.office_desk_pdu_switch_5"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_5"

# Office Desk PDU Switch 5 Off
office_desk_pdu_switch_5_off:
  alias: "Office Desk PDU Switch 5 - Off"
  sequence:
    - service: switch.turn_off
      target:
        entity_id: "switch.office_desk_pdu_switch_5"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_5"

# Office Desk PDU Switch 6 On
office_desk_pdu_switch_6_on:
  alias: "Office Desk PDU Switch 6 - On"
  sequence:
    - service: switch.turn_on
      target:
        entity_id: "switch.office_desk_pdu_switch_6"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_6"

# Office Desk PDU Switch 6 Off
office_desk_pdu_switch_6_off:
  alias: "Office Desk PDU Switch 6 - Off"
  sequence:
    - service: switch.turn_off
      target:
        entity_id: "switch.office_desk_pdu_switch_6"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_6"

# Office Desk PDU Switch 7 On
office_desk_pdu_switch_7_on:
  alias: "Office Desk PDU Switch 7 - On"
  sequence:
    - service: switch.turn_on
      target:
        entity_id: "switch.office_desk_pdu_switch_7"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_7"

# Office Desk PDU Switch 7 Off
office_desk_pdu_switch_7_off:
  alias: "Office Desk PDU Switch 7 - Off"
  sequence:
    - service: switch.turn_off
      target:
        entity_id: "switch.office_desk_pdu_switch_7"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_7"

# Office Desk PDU Switch 8 On
office_desk_pdu_switch_8_on:
  alias: "Office Desk PDU Switch 8 - On"
  sequence:
    - service: switch.turn_on
      target:
        entity_id: "switch.office_desk_pdu_switch_8"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_8"

# Office Desk PDU Switch 8 Off
office_desk_pdu_switch_8_off:
  alias: "Office Desk PDU Switch 8 - Off"
  sequence:
    - service: switch.turn_off
      target:
        entity_id: "switch.office_desk_pdu_switch_8"
    - delay:
        milliseconds: 500
    - service: homeassistant.update_entity
      target:
        entity_id: "switch.office_desk_pdu_switch_8"
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

  # ---------- SNMP Switches ---------- #

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

   # ---------- Dashboard Switches ---------- #
  - platform: template
    switches:

      # Office Desk PDU Switch 1 Refresh
      office_desk_pdu_switch_1_refresh:
        friendly_name: "Office Desk PDU Switch 1"
        value_template: "{{ is_state('switch.office_desk_pdu_switch_1', 'on') }}"
        turn_on:
          service: script.office_desk_pdu_switch_1_on
        turn_off:
          service: script.office_desk_pdu_switch_1_off

      # Office Desk PDU Switch 2 Refresh
      office_desk_pdu_switch_2_refresh:
        friendly_name: "Office Desk PDU Switch 2"
        value_template: "{{ is_state('switch.office_desk_pdu_switch_2', 'on') }}"
        turn_on:
          service: script.office_desk_pdu_switch_2_on
        turn_off:
          service: script.office_desk_pdu_switch_2_off

      # Office Desk PDU Switch 3 Refresh
      office_desk_pdu_switch_3_refresh:
        friendly_name: "Office Desk PDU Switch 3"
        value_template: "{{ is_state('switch.office_desk_pdu_switch_3', 'on') }}"
        turn_on:
          service: script.office_desk_pdu_switch_3_on
        turn_off:
          service: script.office_desk_pdu_switch_3_off

      # Office Desk PDU Switch 4 Refresh
      office_desk_pdu_switch_4_refresh:
        friendly_name: "Office Desk PDU Switch 4"
        value_template: "{{ is_state('switch.office_desk_pdu_switch_4', 'on') }}"
        turn_on:
          service: script.office_desk_pdu_switch_4_on
        turn_off:
          service: script.office_desk_pdu_switch_4_off

      # Office Desk PDU Switch 5 Refresh
      office_desk_pdu_switch_5_refresh:
        friendly_name: "Office Desk PDU Switch 5"
        value_template: "{{ is_state('switch.office_desk_pdu_switch_5', 'on') }}"
        turn_on:
          service: script.office_desk_pdu_switch_5_on
        turn_off:
          service: script.office_desk_pdu_switch_5_off

      # Office Desk PDU Switch 6 Refresh
      office_desk_pdu_switch_6_refresh:
        friendly_name: "Office Desk PDU Switch 6"
        value_template: "{{ is_state('switch.office_desk_pdu_switch_6', 'on') }}"
        turn_on:
          service: script.office_desk_pdu_switch_6_on
        turn_off:
          service: script.office_desk_pdu_switch_6_off

      # Office Desk PDU Switch 7 Refresh
      office_desk_pdu_switch_7_refresh:
        friendly_name: "Office Desk PDU Switch 7"
        value_template: "{{ is_state('switch.office_desk_pdu_switch_7', 'on') }}"
        turn_on:
          service: script.office_desk_pdu_switch_7_on
        turn_off:
          service: script.office_desk_pdu_switch_7_off

      # Office Desk PDU Switch 8 Refresh
      office_desk_pdu_switch_8_refresh:
        friendly_name: "Office Desk PDU Switch 8"
        value_template: "{{ is_state('switch.office_desk_pdu_switch_8', 'on') }}"
        turn_on:
          service: script.office_desk_pdu_switch_8_on
        turn_off:
          service: script.office_desk_pdu_switch_8_off
```
