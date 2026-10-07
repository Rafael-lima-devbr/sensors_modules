# Wokwi Sensor Reading Examples

Embedded C/C++ examples for **ESP32 sensor simulation in Wokwi**, focused on sensor acquisition, data processing, filtering and alert-state logic.

**Status:** Study and prototyping repository

## Simulation preview

<p align="center">
  <a href="https://wokwi.com/projects/468739374813374465">
    <img width="90%" alt="ESP32 multi-sensor simulation in Wokwi" src="https://github.com/user-attachments/assets/93a9d101-e926-4739-8ddc-da26c0e2c27f" />
  </a>
</p>

<p align="center">
  <a href="https://wokwi.com/projects/468739374813374465"><strong>Open the interactive simulation in Wokwi</strong></a>
</p>

## Sensors

| Sensor | Variable | Interface |
|---|---|---|
| BMP180 | Atmospheric pressure | I²C |
| HC-SR04 | Distance | Trigger / Echo GPIO |
| DS18B20 | Temperature | 1-Wire |
| MQ-2 | Estimated gas concentration | ADC |

## Structure

```text
.
├── BMP180/
│   └── BMP180.ino
├── HC-SR04/
│   └── HC-SR04.ino
├── DS18B20/
│   └── DS18B20.ino
└── MQ2/
    └── MQ2.ino
```

Each directory contains an independent example for one simulated sensor. Wokwi projects may also include `diagram.json` and `libraries.txt` when needed.

## What the examples practice

- ESP32 GPIO configuration
- I²C communication
- 1-Wire communication
- analog-to-digital conversion
- ultrasonic distance measurement
- sensor-data acquisition
- moving-average filtering
- state classification
- serial monitoring and debugging

## Pin Configuration

| Component | ESP32 Pin |
|---|---:|
| DS18B20 data | GPIO 4 |
| BMP180 SDA | GPIO 21 |
| BMP180 SCL | GPIO 22 |
| HC-SR04 Trigger | GPIO 18 |
| HC-SR04 Echo | GPIO 5 |
| MQ-2 analog output | GPIO 33 |

The pin configuration must match each Wokwi `diagram.json`.

## Running in Wokwi

1. Open the [shared Wokwi project](https://wokwi.com/projects/468739374813374465), or create/import an ESP32 project.
2. Add the source code from the desired sensor example.
3. Configure the simulated component and wiring.
4. Add external libraries when required.
5. Start the simulation.
6. Use the Serial Monitor to inspect readings.

## Moving-Average Filter

Some examples smooth measurements using a moving window of up to 15 readings. The filter is used to reduce abrupt variations in simulated temperature, pressure and gas measurements.

The distance measurement can remain unfiltered when a faster response is preferable.

## MQ-2 Simulation

The MQ-2 example converts the simulated ESP32 ADC reading into an estimated gas-concentration value using a nonlinear curve adjusted for the Wokwi simulation.

This conversion is specific to the simulated environment and **must not be interpreted as a calibrated physical MQ-2 measurement**.

A real MQ-2 requires physical calibration and is affected by factors such as reference gas, sensor resistance, load resistance, temperature and humidity.

## Operational States

The examples can classify simulated conditions into states such as:

- `NORMAL`
- `ATENÇÃO`
- `CRÍTICO`

The thresholds are intended to demonstrate alert logic and not to represent certified industrial exposure limits.

## Limitations

- Wokwi does not reproduce every characteristic of physical sensors.
- ADC behavior may differ from real hardware.
- Simulated calibration does not replace physical calibration.
- The MQ-2 ppm estimate is specific to this project.
- The examples are for learning and prototyping, not certified industrial-safety use.

## License

MIT License.
