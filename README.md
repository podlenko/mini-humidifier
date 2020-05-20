# Mini Humidifier Card for Xiaomi Smartmi Zhimi Air Humidifier

[![Last Version](https://img.shields.io/github/package-json/v/artem-sedykh/mini-humidifier?label.svg=release)](https://github.com/artem-sedykh/mini-humidifier/releases/latest)
[![Build Status](https://travis-ci.com/artem-sedykh/mini-humidifier.svg?branch=master)](https://travis-ci.com/artem-sedykh/mini-humidifier)
[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/artem-sedykh/mini-humidifier)
[![buymeacoffee_badge](https://img.shields.io/badge/Donate-buymeacoffe-ff813f?style=flat)](https://www.buymeacoffee.com/anavrin72)

Tested on [zhimi.humidifier.cb1](https://www.home-assistant.io/integrations/fan.xiaomi_miio/)

A minimalistic yet customizable humidifier card for [Home Assistant](https://github.com/home-assistant/home-assistant) Lovelace UI.

Inspired by [mini media player](https://github.com/kalkih/mini-media-player).

![Preview Image](https://user-images.githubusercontent.com/861063/79672681-0f241580-81dd-11ea-913c-234c287a6264.png)

## Install

*This card is available in [HACS](https://github.com/custom-components/hacs) (Home Assistant Community Store)*

### Simple install

1. Download and copy `mini-humidifier-bundle.js` from the [latest release](https://github.com/artem-sedykh/mini-humidifier/releases/latest) into your `config/www` directory.

2. Add a reference to `mini-humidifier-bundle.js` inside your `ui-lovelace.yaml`.

  ```yaml
  resources:
    - url: /local/mini-humidifier-bundle.js?v=1.0.9
      type: module
  ```

### CLI install

1. Move into your `config/www` directory

2. Grab `mini-humidifier-bundle.js`

  ```console
  $ wget https://github.com/artem-sedykh/mini-humidifier/releases/download/v1.0.1/mini-humidifier-bundle.js
  ```

3. Add a reference to `mini-humidifier-bundle.js` inside your `ui-lovelace.yaml`.

  ```yaml
  resources:
    - url: /local/mini-humidifier-bundle.js?v=1.0.9
      type: module
  ```

## Updating
1. Find your `mini-humidifier-bundle.js` file in `config/www` or wherever you ended up storing it.

2. Replace the local file with the latest one attached in the [latest release](https://github.com/artem-sedykh/mini-humidifier/releases/latest).

3. Add the new version number to the end of the cards reference url in your `ui-lovelace.yaml` like below.

  ```yaml
  resources:
    - url: /local/mini-humidifier-bundle.js?v=1.0.9
      type: module
  ```

*You may need to empty the browsers cache if you have problems loading the updated card.*

## Using the card

### Options

#### Card options
| Name | Type | Default | Since | Description |
|------|------|---------|-------|-------------|
| type | string | **required** | v1.0.1 | `custom:mini-humidifier`
| entity | string | **required** | v1.0.1 | An entity_id from an entity within the `fan` domain.
| name | string | optional | v1.0.1 | Override the entities friendly name.
| icon | string | optional | v1.0.1 | Specify a custom icon from any of the available mdi icons.
| group | boolean | optional | v1.0.1 | Removes paddings, background color and box-shadow.
| **power_button** | object | optional | v1.0.3 | Power button, [example](#power-button-configuration).
| power_button: `type` | string | optional | v1.0.3 | `toggle` or `button`, default `mdi:power`
| power_button: `icon` | string | optional | v1.0.3 | Custom icon for type `buttom`, default value `mdi:fan`
| power_button: `hide` | boolean | optional | v1.0.3 | Hide button, default value `False`
| **dry_button** | object | optional | v1.0.1 | Dry mode on/off button
| dry_button: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:weather-sunny`
| dry_button: `hide` | boolean | optional | v1.0.1 | Hide button, default value `False`
| dry_button: `order` | number | optional | v1.0.1 | Sort order, default value `0`
| **fan_mode_button** | object | optional | v1.0.1 | Dry mode on/off button
| fan_mode_button: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:fan`
| fan_mode_button: `hide` | boolean | optional | v1.0.1 | Hide button, default value `False`
| fan_mode_button: `order` | number | optional | v1.0.1 | Sort order, default value `1`
| fan_mode_button: `source` | object | optional | v1.0.1 | Source for fan mode drop down list, [example](#fan-mode-source).
| fan_mode_button: `source: auto` | object | optional | v1.0.6 | auto mode configuration
| fan_mode_button: `source: auto: value` | string | optional | v1.0.6 | value, default `Auto`
| fan_mode_button: `source: auto: name` | string | optional | v1.0.6 | Display name, default `Auto`
| fan_mode_button: `source: auto: order` | number | optional | v1.0.6 | Sort order, default `0`
| fan_mode_button: `source: auto: hide` | boolean | optional | v1.0.6 | Hide from dropdown list, default `False`
| fan_mode_button: `source: silent` | object | optional | v1.0.6 | silent mode configuration
| fan_mode_button: `source: silent: value` | string | optional | v1.0.6 | value, default `Silent`
| fan_mode_button: `source: silent: name` | string | optional | v1.0.6 | Display name, default `Silent`
| fan_mode_button: `source: silent: order` | number | optional | v1.0.6 | Sort order, default `1`
| fan_mode_button: `source: silent: hide` | boolean | optional | v1.0.6 | Hide from dropdown list, default `False`
| fan_mode_button: `source: medium` | object | optional | v1.0.6 | medium mode configuration
| fan_mode_button: `source: medium: value` | string | optional | v1.0.6 | value, default `Medium`
| fan_mode_button: `source: medium: name` | string | optional | v1.0.6 | Display name, default `Medium`
| fan_mode_button: `source: medium: order` | number | optional | v1.0.6 | Sort order, default `2`
| fan_mode_button: `source: medium: hide` | boolean | optional | v1.0.6 | Hide from dropdown list, default `False`
| fan_mode_button: `source: high` | object | optional | v1.0.6 | high mode configuration
| fan_mode_button: `source: high: value` | string | optional | v1.0.6 | value, default `High`
| fan_mode_button: `source: high: name` | string | optional | v1.0.6 | Display name, default `High`
| fan_mode_button: `source: high: order` | number | optional | v1.0.6 | Sort order, default `3`
| fan_mode_button: `source: high: hide` | boolean | optional | v1.0.6 | Hide from dropdown list, default `False`
| fan_mode_button: `source: strong` | object | optional | v1.0.7 | strong mode configuration, for `ZHIMI.HUMIDIFIER.V1`
| fan_mode_button: `source: strong: value` | string | optional | v1.0.7 | value, default `High`
| fan_mode_button: `source: strong: name` | string | optional | v1.0.7 | Display name, default `Strong`
| fan_mode_button: `source: strong: order` | number | optional | v1.0.7 | Sort order, default `4`
| fan_mode_button: `source: strong: hide` | boolean | optional | v1.0.7 | Hide from dropdown list, default `True`
| **led_button** | object | optional | v1.0.1 | Button Illumination on/off
| led_button: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:lightbulb-on-outline`
| led_button: `hide` | boolean | optional | v1.0.1 | Hide button, default value `False`
| led_button: `order` | number | optional | v1.0.1 | Sort order, default value `2`
| led_button: `type` | string | optional | v1.0.2 | Render type, available values `button or dropdown` default value `button`
| led_button: `source` | object | optional | v1.0.2 | Source for dropdown button type, supported values are 0 (Bright), 1 (Dim), 2 (Off), [example](#led-button-dropdown-list-configuration).
| led_button: `source:bright` | object | optional | v1.0.2 | 0 (Bright)
| led_button: `source:bright:value` | number | optional | v1.0.2 | Bright value, default `0`
| led_button: `source:bright:name` | string | optional | v1.0.2 | name, default `Bright`
| led_button: `source:bright:order` | number | optional | v1.0.2 | Sort order, default `0`
| led_button: `source:dim` | object | optional | v1.0.2 | 1 (Dim)
| led_button: `source:dim:value` | number | optional | v1.0.2 | Dim value, default `1`
| led_button: `source:dim:name` | string | optional | v1.0.2 | name, default `Dim`
| led_button: `source:dim:order` | number | optional | v1.0.2 | Sort order, default `1`
| led_button: `source:'off'` | object | optional | v1.0.2 | 2 (Off), the key must be written in quotation marks, without them the parameter will be false
| led_button: `source:'off':value` | string | optional | v1.0.2 | Off value, default `2`
| led_button: `source:'off':name` | string | optional | v1.0.2 | name, default `Off`
| led_button: `source:'off':order` | number | optional | v1.0.2 | Sort order, default `2`
| **buzzer_button** | object | optional | v1.0.1 | Buzzer on/off
| buzzer_button: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:bell-outline`
| buzzer_button: `hide` | boolean | optional | v1.0.1 | Hide button, default value `False`
| buzzer_button: `order` | number | optional | v1.0.1 | Sort order, default value `3`
| **child_lock_button** | object | optional | v1.0.1 | Child lock on/off
| child_lock_button: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:lock`
| child_lock_button: `hide` | boolean | optional | v1.0.1 | Hide button, default value `False`
| child_lock_button: `order` | number | optional | v1.0.1 | Sort order, default value `4`
| **toggle_button** | object | optional | v1.0.1 | Toggle button.
| toggle_button: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:dots-horizontal`
| toggle_button: `hide` | boolean | optional | v1.0.1 | Hide button, default value `False`
| toggle_button: `default` | boolean | optional | v1.0.5 | Default toggle_button state, default value `off`, [example](#always-show-control-buttons).
| **depth** | object | optional | v1.0.1 | Information indicator, showing how much water is left in the humidifier
| depth: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:beaker-outline`
| depth: `icon_template` | string | optional | v1.0.8 | Custom icon template, context values: `depth`(calculated value) and `raw`(raw depth value) [example](#icon-template-example)
| depth: `hide` | boolean | optional | v1.0.1 | Hide indicator, default value `False`
| depth: `order` | number | optional | v1.0.1 | Indicator sort order, default value `0`
| depth: `unit_type` | string | optional | v1.0.1 | Indicator type available Values: `liters` or `percent`, default `percent`
| depth: `unit` | string | optional | v1.0.1 | display unit, default `%`
| depth: `max_value` | number | optional | v1.0.1 | Depth attribute value with a full tank of humidifier, default `125`
| depth: `volume` | number | optional | v1.0.1 | Humidifier tank volume, needed to calculate values in liters, default `4` liters
| depth: `fixed` | number | optional | v1.0.1 | Rounding the calculated values, default value `0`
| **temperature** | object | optional | v1.0.1 | Information indicator, showing temperature
| temperature: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:thermometer-low`
| temperature: `icon_template` | string | optional | v1.0.8 | Custom icon template, context value: `temperature`
| temperature: `hide` | boolean | optional | v1.0.1 | Hide indicator, default value `False`
| temperature: `order` | number | optional | v1.0.1 | Indicator sort order, default value `1`
| temperature: `unit` | string | optional | v1.0.1 | display unit, default `°C`
| temperature: `fixed` | number | optional | v1.0.7 | Rounding the calculated values, default value `1`
| temperature: `source` | object | optional | v1.0.6 | data source, by default, data taken from the attribute `temperature` [examples](#temperature-source-examples).
| temperature: `source: entity` | string | optional | v1.0.6 | custom entity, if the attribute is not set, the state value
| temperature: `source: attribute` | string | optional | v1.0.6 | if the entity parameter is not set, then the data will be obtained from the specified entity attribute, otherwise from the current entity attribute
| **humidity** | object | optional | v1.0.1 | Information indicator, showing humidity
| humidity: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:water-outline`
| humidity: `icon_template` | string | optional | v1.0.8 | Custom icon template, context value: `humidity`
| humidity: `hide` | boolean | optional | v1.0.1 | Hide indicator, default value `False`
| humidity: `order` | number | optional | v1.0.1 | Indicator sort order, default value `2`
| humidity: `unit` | string | optional | v1.0.1 | display unit, default `%`
| humidity: `fixed` | number | optional | v1.0.7 | Rounding the calculated values, default value `1`
| humidity: `source` | object | optional | v1.0.6 | data source, by default, data taken from the attribute `humidity`
| humidity: `source: entity` | string | optional | v1.0.6 | custom entity, if the attribute is not set, the state value
| humidity: `source: attribute` | string | optional | v1.0.6 | if the entity parameter is not set, then the data will be obtained from the specified entity attribute, otherwise from the current entity attribute
| **target_humidity** | object | optional | v1.0.1 | Target humidity
| target_humidity: `icon` | string | optional | v1.0.1 | Custom icon, default value `mdi:water-outline`
| target_humidity: `icon_template` | string | optional | v1.0.8 | Custom icon template, context value: `targetHumidity`
| target_humidity: `hide` | boolean | optional | v1.0.1 | Hide indicator, default value `False`
| target_humidity: `unit` | string | optional | v1.0.1 | display unit, default `%`
| target_humidity: `min` | number | optional | v1.0.1 | minimum target humidity, default value `30` [see](https://www.home-assistant.io/integrations/fan.xiaomi_miio/)
| target_humidity: `max` | number | optional | v1.0.1 | maximum target humidity, default value `80` [see](https://www.home-assistant.io/integrations/fan.xiaomi_miio/)
| target_humidity: `step` | number | optional | v1.0.1 | slider step, default value `10`
| scale | number | optional | v1.0.3 | UI scale modifier, default is `1`.
| tap_action | [action object](#action-object-options) | true | v1.0.4 | Action on click/tap, [examples](#action-object-options-examples).

#### Action object options
| Name | Type | Default | Options | Description |
|------|:----:|:-------:|:-----------:|-------------|
| action | string | `more-info` | `more-info` / `navigate` / `call-service`  / `url` / `none` / `toggle` | Action to perform.
| entity | string |  | Any entity id | Override default entity of `more-info`, when  `action` is defined as `more-info`.
| service | string |  | Any service | Service to call (e.g. `fan.turn_on`) when `action` is defined as `call-service`
| service_data | object |  | Any service data | Service data to include with the service call (e.g. `entity_id: fan.xiaomi_miio_device`)
| navigation_path | string |  | Any path | Path to navigate to (e.g. `/lovelace/0/`) when `action` is defined as `navigate`.
| url | string |  | Any URL | URL to open when `action` is defined as `url`.

### Theme variables
The following variables are available and can be set in your theme to change the appearence of the card.
Can be specified by color name, hexadecimal, rgb, rgba, hsl, hsla, basically anything supported by CSS.

| name | Default | Description |
|------|---------|-------------|
| mini-humidifier-name-font-weight | 400 | Font weight of the entity name
| mini-humidifier-info-font-weight | 300 | Font weight of the states
| mini-humidifier-icon-color | --mini-humidifier-base-color, var(--paper-item-icon-color, #44739e) | The color for icons
| mini-humidifier-button-color |--mini-humidifier-button-color, var(--paper-item-icon-color, #44739e) | The color for buttons icons
| mini-humidifier-accent-color | var(--accent-color) | The accent color of UI elements
| mini-humidifier-base-color | var(--primary-text-color) & var(--paper-item-icon-color) | The color of base text
| mini-humidifier-background-opacity | 1 | Opacity of the background
| mini-humidifier-scale | 1 | Scale of the card


### Example usage

#### Basic card
<img src="https://user-images.githubusercontent.com/861063/79479945-27960380-8016-11ea-8110-5460566feb0b.png" width="500px" alt="Basic card example" />  

```yaml
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
```

#### Entity card
For use Entities card you need to add `group: on`

<img src="https://user-images.githubusercontent.com/861063/79480184-75127080-8016-11ea-8b0b-c102bf26a5d6.png" width="500px" alt="Entities card example" />


```yaml
- type: entities
  title: Entities
  state_color: true
  entities:
    - type: custom:mini-humidifier
      entity: fan.xiaomi_miio_device
      group: on

    - entity: switch.living_room_wall_switch_right
```

#### Fan mode source 

```yaml
# Abbreviated record, override name only
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  fan_mode_button:
    source:
      auto: Авто
      silent: Тихий
      medium: Средний
      high: Высокоий

# Full record to override other parameters
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  fan_mode_button:
    source:
      auto:
        name: Авто
        order: 4
```


#### Led button dropdown list configuration


<img src="https://user-images.githubusercontent.com/861063/79615043-7a50e780-810a-11ea-8716-f96f868be879.png" width="500px" alt="led button dropdown list" />

```yaml
# Abbreviated record, override name only
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  led_button:
    type: dropdown
    source:
      bright: 'Bright'
      dim: 'Dim'
      'off': 'Off'

# Full record to override other parameters
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  led_button:
    type: dropdown
    source:
      bright:
        name: Bright
        order: 2
      dim:
        name: Dim
        order: 1
      'off':
        name: 'Off'
        order: 0
```



#### Power button configuration


<img src="https://user-images.githubusercontent.com/861063/79672736-6924db00-81dd-11ea-9920-cdf0661b567c.png" width="500px" alt="power button configuration" />

```yaml
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  power_button:
    type: button
    icon: mdi:power
```



#### Action object options examples

```yaml
# toggle example
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  tap_action:
    action: toggle

# call-service example
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  tap_action:
    action: call-service
    service: xiaomi_miio.fan_set_led_brightness
    service_data:
      brightness: 1

# navigate example
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  tap_action:
    action: navigate
    navigation_path: '/lovelace/4'

# navigate example
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  tap_action:
    action: url
    url: 'https://www.google.com/'

# none example
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  tap_action: none

# more-info for custom entity example
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  tap_action:
    action: more-info
    entity: sensor.humidity_158d000444c824
```


#### Always show control buttons


<img src="https://user-images.githubusercontent.com/861063/79689322-af6d4f00-825c-11ea-9e95-9e66fbb1b58f.png" width="500px" alt="Always show control buttons" />

```yaml
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  toggle_button:
    hide: on
    default: on
  power_button:
    type: button
    icon: mdi:power
```


#### Temperature source examples


```yaml
# Display temperature using sensor
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  temperature:
    source:
      entity: sensor.temperature

# Display temperature from custom attribute
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  temperature:
    source:
      attribute: use_time

# Using entity and attribute, display the sensor battery level for example
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  temperature:
    unit: '%'
    icon: 'mdi:battery'
    source:
      entity: sensor.temperature
      attribute: battery_level
```


#### ZHIMI.HUMIDIFIER.V1 configuration


```yaml
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
# hide the indicator showing the amount of water
  depth:
    hide: on
# hide dry button
  dry_button:
    hide: on
  fan_mode_button:
    source:
# hide auto mode option
      auto:
        hide: on
# show strong option
      strong:
        hide: off
```


#### icon template example

when changing `depth` value we change the icon
```yaml
- type: custom:mini-humidifier
  entity: fan.xiaomi_miio_device
  depth:
    icon_template: >
      {% if depth < 10 %}
        <ha-icon class='state__value_icon' icon='mdi:tray-alert' style='color: #bd1c1c;'></ha-icon>
      {% elseif depth < 45 %}
        <ha-icon class='state__value_icon' icon='mdi:tray-minus'></ha-icon>
      {% else %}
        <ha-icon class='state__value_icon' icon='mdi:tray-full'></ha-icon>
      {% endif %}
```
used plugin [jinja-js](https://github.com/sstur/jinja-js)

<img src="https://user-images.githubusercontent.com/861063/82473688-a1685380-9ad2-11ea-9f7f-ba094f1e2d27.png"  alt="expample"/>


## Development
*If you plan to contribute back to this repo, please fork & create the PR against the [dev](https://github.com/artem-sedykh/mini-humidifier/tree/dev) branch.*

**Clone this repository into your `config/www` folder using git.**

 ```console
$ git clone https://github.com/artem-sedykh/mini-humidifier.git
```

**Add a reference to the card in your `ui-lovelace.yaml`.**

```yaml
resources:
  - url: /local/mini-humidifier/dist/mini-humidifier-bundle.js
    type: module
```

### Instructions

*Requires `nodejs` & `npm`*

1. Move into the `mini-humidifier` repo, checkout the *dev* branch & install dependencies.
```console
$ cd mini-humidifier-dev && git checkout dev && npm install
```

2. Make changes to the source

3. Build the source by running
```console
$ npm run build
```

4. Refresh the browser to see changes

    *Make sure cache is cleared or disabled*

5. *(Optional)* Watch the source and automatically rebuild on save
```console
$ npm run watch
```

*The new `mini-humidifier-bundle.js` will be build and ready inside `/dist`.*


## Getting errors?
Make sure you have `javascript_version: latest` in your `configuration.yaml` under `frontend:`.

Make sure you have the latest version of `mini-humidifier-bundle.js`.

If you have issues after updating the card, try clearing your browsers cache or restart Home Assistant.

If you are getting "Custom element doesn't exist: mini-humidifier" or running older browsers try replacing `type: module` with `type: js` in your resource reference, like below.

```yaml
resources:
  - url: ...
    type: js
```

## Inspiration
- [@kalkih](https://github.com/kalkih) - [mini-media-player](https://github.com/kalkih/mini-media-player)

## License
This project is under the MIT license.
