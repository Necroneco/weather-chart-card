<h1 align="center">Weather Chart Card</h1>
<p align="center">
  <a href="https://github.com/custom-components/hacs">
    <img src="https://img.shields.io/badge/HACS-Default-orange.svg" />
  </a>
</p>

![image](https://github.com/mlamberts78/weather-chart-card/assets/93537082/2f35383c-a566-4035-9cc3-6b70d2c461d0)

## Installation

### HACS (recommended)

This card is available in [HACS](https://hacs.xyz/) (Home Assistant Community Store).
<small>_HACS is a third party community store and is not included in Home Assistant out of the box._</small>

### Manual install

1. Download and copy `weather-chart-card.js` from the [latest release](https://github.com/mlamberts78/weather-chart-card/releases/latest) into your `config/www` directory.

2. Add the resource reference as decribed below.

3. Add the resource reference as decribed below.

Add a reference to the copied file inside your `configuration.yaml` or in the Home Assistant UI:

[![Open your Home Assistant instance and show your Lovelace resources.](https://my.home-assistant.io/badges/lovelace_resources.svg)](https://my.home-assistant.io/redirect/lovelace_resources/)
```yaml
# Example Lovelace UI config entry
resources:
- type: module
  url: /local/weather-chart-card.js
```
Then you can add the card to the view:
```yaml
# Example Lovelace UI config entry
type: custom:weather-chart-card
entity: weather.home
```

#### Configuration variables:

##### Card options

| Name                 | Type    | Default                  | Description                                                                                        |
| -------------------- | ------- | -------------------------|--------------------------------------------------------------------------------------------------- |
| type                 | string  | **Required**             | Should be `custom:weather-chart-card`.                                                             |
| entity               | string  | **Required**             | An entity_id with the `weather` domain.                                                            |
| temp                 | string  | none                     | An entity_id for a custom temperature sensor.                                                      |
| press                | string  | none                     | An entity_id for a custom pressure sensor.                                                         |
| humid                | string  | none                     | An entity_id for a custom humidity sensor.                                                         |
| title                | string  | none                     | Card title.                                                                                        |
| show_main            | boolean | true                     | Show or hide a section with current weather condition and temperature.                             |
| show_attributes      | boolean | true                     | Show or hide a section with attributes such as pressure, humidity, wind direction and speed, etc.  |
| show_humid           | boolean | true                     | Show or hide humidity on the card.                                                                 |
| show_pressure        | boolean | true                     | Show or hide pressure on the card.                                                                 |
| show_wind_direction  | boolean | true                     | Show or hide wind_direction on the card.                                                           |
| show_wind_speed      | boolean | true                     | Show or hide wind_speed on the card.                                                               |
| icons                | string  | none                     | Path to the location of custom icons in svg format, for example `/local/weather-icons/`.           |
| icons_size           | number  | 25                       | The size of custom icons in pixels.                                                                |
| forecast             | object  | none                     | See [forecast options](#forecast-options) for available options.                                   |
| units                | object  | none                     | See [units of measurement](#units-of-measurement) for available options.                           |

##### Forecast options

| Name                 | Type    | Default                  | Description                                                                                        |
| -------------------- | ------- | -------------------------|--------------------------------------------------------------------------------------------------- |
| labels_font_size     | string  | 11                       | Font size for temperature and precipitation labels.                                                |
| temperature1_color   | string  | rgba(255, 152, 0, 1.0)   | Temperature first line chart color.                                                                |
| temperature2_color   | string  | rgba(68, 115, 158, 1.0)  | Temperature second line chart color.                                                               |
| precipitation_color  | string  | rgba(132, 209, 253, 1.0) | Precipitation bar chart color.                                                                     |
| condition_icons      | boolean | true                     | Show or hide forecast condition icons.                                                             |
| show_wind_forecast   | boolean | true                     | Show or hide wind forecast on the card.                                                            |

##### Units of measurement

| Name                 | Type    | Default                  | Description                                                                                        |
| -------------------- | ------- | -------------------------|--------------------------------------------------------------------------------------------------- |
| pressure             | string  | 'hPa'                    | Can be 'hPa' or 'mmHg'                                                                             |
| speed                | string  | 'km/h'                   | Can be 'km/h' or 'm/s'                                                                             |

###### What custom icons can I use?
Icons should be in svg format. Icons should have names as shown [here](https://github.com/mlamberts78/weather-chart-card/blob/master/src/const.js#L24). Example:
![130360372-76d70c42-986c-46e3-b9b5-810f0317f94f](https://github.com/mlamberts78/weather-chart-card/assets/93537082/d3ee55a2-e64f-4354-b36d-9faf6ea37361)

#### Example usage:
###### Basic
![hourly](https://github.com/mlamberts78/weather-chart-card/assets/93537082/499df59b-3c1a-42c0-8540-e62a15467cbe)
```yaml
type: custom:weather-chart-card
entity: weather.home_hourly
```
###### Chart only
![Chart-only](https://github.com/mlamberts78/weather-chart-card/assets/93537082/45f118c9-d71f-4494-9b78-46d1321b3270)
```yaml
type: custom:weather-chart-card
entity: weather.openweathermap
show_main: false
show_attributes: false
forecast:
  condition_icons: false
```

###### Custom units
![Custom-units](https://github.com/mlamberts78/weather-chart-card/assets/93537082/dfec83d5-285a-48fe-970b-e33ad5bb2429)
```yaml
type: custom:weather-chart-card
entity: weather.openweathermap
units:
  pressure: mmHg
  speed: m/s
```

###### Supported languages:
Czech <br />
German <br />
Dutch <br />
English <br />
Spanish <br />
Finnish <br />
Hungarian <br />
Russian <br />
Swedish <br />
French <br />
Polish
