# Gauge card

A simple gauge implemented in CSS based on https://github.com/JohnrBell/Gauge_CSS.

![gauge-card](https://user-images.githubusercontent.com/7738048/42317998-73070c5e-8056-11e8-8621-49c61b5b7be5.gif)

![bedroom-temperature](https://user-images.githubusercontent.com/7738048/42344596-806b4a82-80a5-11e8-8e92-9077ad749dfe.gif)


**Options**

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| type | string | **Required** | `custom:gauge-card`
| title | string | optional | Name to display on card
| entity | string | **Required** | `sensor.my_temperature`
| min | number | 0 | Minimum value for graph
| max | number | 100 | Maximum value for graph
| scale | string | '50px' | Base value for graph visual size
| severity | object | optional | Severity object. See below

Severity object

| Name | Type | Default | Description
| ---- | ---- | ------- | -----------
| red | number | **Required** | Value from which to start red color
| green | number | **Required** | Value from which to start green color
| amber | number | **Required** | Value from which to start amber color
| normal | number | **Required** | Value from which to start blue color

*N.B. three of the above must be used, i.e. (red/green/normal) or (red/amber/green)

**Example**

Using two with stack
```yaml
- type: horizontal-stack
  cards:
    - type: custom:gauge-card
      title: Temperature
      entity: sensor.random_temperature
      min: -20
      max: 35
    - type: custom:gauge-card
      title: Oil
      entity: sensor.my_oil_sensor
      severity:
        red: 50
        green: 0
        amber: 40
```

Simple one
```yaml
- type: custom:gauge-card
  entity: sensor.my_oil_sensor
  scale: 100px
```
