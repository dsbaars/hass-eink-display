HASS eInk Display
=================

An small eInk display for smart homes powered by [Home Assistant](https://www.home-assistant.io/).

![Photo of eInk display](/media/hat_on_pi.jpg)

Note: It is still very 'hacky'. I made this in two hours with rusty Python experience.

#### Hardware requirements
- Raspberry Pi 3B (Others should also work)
- Waveshare eInk HAT (I used a 2.13 inch since it fits nicely on a Zero W) (bought on [AliExpress]( https://nl.aliexpress.com/item/212x104-2-13inch-E-Ink-display-HAT-for-Raspberry-Pi-Red-black-white-three-color-SPI/32829497666.html)
)

#### Software prerequisites
- Home Assistant with the [Websocket API enabled](https://developers.home-assistant.io/docs/en/external_api_websocket.html)
- All [required libraries for the Waveshare e-Paper HAT](https://www.waveshare.com/wiki/2.13inch_e-Paper_HAT#Working_with_Raspberry_Pi)

#### Design rationale
Create a two threaded Python 3 script which:
- Has one thread connecting to the HASS WebSocket API and listen for state changes
- Has another thread for updating the eInk display when state changes and updates the time.

The display shows:

__Left side__:
All rooms (abbreviated) in a table, with a row showing if the lights are on, and another row showing the temperature.

__Right side__:
Top: Power consumption and living room temperature<br>
Bottom: Date and time

#### Hardware which feeds HA (relevant for this project)
- [Tado](https://www.tado.com/) Smart Thermostat 
Smart Thermostat for living room and smart radiator thermostat for attic rooms
- Xiaomi Mijia Bluetooth Thermometer/Hygrometer (from [AliExpress](https://nl.aliexpress.com/item/Xiaomi-Mijia-Bluetooth-Hygrothermograph-Hoge-Gevoelige-Hygrometer-Thermometer-Lcd-scherm-Smart-Home-Temperatuur-Vochtigheid-Sensor/32846083629.html)) 
For all other rooms, sends temperature and humidity over bluetooth
- Smart meter connected using [P1 SMR](https://www.home-assistant.io/components/sensor.dsmr/)


