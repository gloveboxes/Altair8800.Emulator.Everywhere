# Cloud Enabled Altair 8800 on Azure Sphere

[Azure Sphere Clould Enabled Altair 8880 Emulator Documentation](https://github.com/AzureSphereCloudEnabledAltair8800/AzureSphereCloudEnabledAltair8800.emulator/wiki)

## Install required libraries

### Raspberry Pi running Raspberry Pi OS (Bullseye)

```bash
sudo apt-get install -y libuv1.dev unzip cmake build-essential gdb curl libcurl4-openssl-dev libssl-dev uuid-dev ca-certificates git mosquitto libi2c-dev
```

### macOS Monterey 12.1


### Windows 10 & 11 with Windows Subsystem for Linux (WSL) 2

### Desktop Linux

## Clone Altair 8800 repo

```bash
git clone --recurse-submodules https://github.com/gloveboxes/Altair8800Linux.git
```


## Build project

```bash
cd Altair8800Linux/AltairHL_emulator
mkdir build
cmake -B build
cmake --build build --config release --target all 
```

## Enable Raspberry I2C Interface

```bash
sudo raspi-config --> interfacing options --> enable i2c
```

## Mosquitto MQTT broker configuration

```bash
sudo nano /etc/mosquitto/conf.d/altair.conf
```

Paste in the following text.

```text
listener 1883 localhost
allow_anonymous true

listener 8080
allow_anonymous true
protocol websockets

```

### Restart Mosquitto MQTT broker

```bash
sudo systemctl restart mosquitto.service
```


## Start Web Server on Raspberry Pi

```bash
python3 -m http.server --cgi 8081
```

## Replacing char in c

https://stackoverflow.com/questions/32496497/standard-function-to-replace-character-or-substring-in-a-char-array/32496721


