# ESP32-S2-INSTALL

<img src="/docs/proof-compileandinstall.png" width="640">

This repo contains scripts to install ESP32-S2 requirements. 

As of this writing (Aug 15th 2020) you cannot install the board Arduino IDE board without alot of messing around. These scrips will make it easy. The reason is because internaly only the ESP-IDF v4.2 will support ESP32-S2 final chip. This is currently available on the ESP-IDF master branch and arduino-esp32 esp32s2 branch only. The below instructions should give you everything you need once you have Ardunio installed.

# To install the ESP32-S2 board into Ardunio on Ubuntu 20.04.1 LTS


Run in a terminal:
````
sudo usermod -a -G dialout $USER && \
sudo apt-get install git && \
wget https://bootstrap.pypa.io/get-pip.py && \
sudo python get-pip.py && \
sudo pip install pyserial && \
mkdir -p ~/Arduino/hardware/espressif && \
cd ~/Arduino/hardware/espressif && \
git clone -b esp32s2 https://github.com/espressif/arduino-esp32.git arduino-esp32s2 && \
cd arduino-esp32s2 && \
git submodule update --init --recursive && \
cd tools && \
python3 get.py && \
cd .. && \
sed -i 's/name=ESP32 Arduino/name=ESP32-S2 Arduino/g' platform.txt 
````

Restart Arduino IDE

Set your board as "ESP32-S2 Arduino -> ESP32S2 Dev Module"


# If you use the Snap version of Ardunio you should also

The Snap package has been broken for the project paths. This will link the default Snap version of the projects directory to your main ~/ folder

Run in a terminal:
```
mkdir -p ~/Arduino
rsync -rav ~/snap/arduino/current/Arduino/ ~/Arduino
rm -r ~/snap/arduino/current/Arduino 
ln -s ~/Arduino ~/snap/arduino/current/ 
```
