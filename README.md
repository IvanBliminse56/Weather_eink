All this work is based on work done by aerodynamics
https://www.hackster.io/aerodynamics/weather-and-news-station-e-paper-and-raspberry-pi-a19fa3#comments
Thank him for his incredible work

Works only on raspberryPi 3 for me so far

Install RaspberryPi OS light 32bit (Won't be described here)
Connect to the Pi via SSH (Won't be described here)

I use the waveshare 7.5inch HD e-Paper HAT (B), can be found on Amazone

For ease of setting up, install following programs on your computer
  WinSCP
  Visual Studio Code

Update and upgrade the pi

sudo apt-get update && sudo apt-get update -y


Pre-requisites  From waveshare
  Enable SPI interface

sudo raspi-config

Interfacing Option > SPI > yes > restart the Pi
sudo reboot

  Install BCM2835 libraries
 
wget http://www.airspayce.com/mikem/bcm2835/bcm2835-1.60.tar.gz
tar zxvf bcm2835-1.60.tar.gz 
cd bcm2835-1.60/
sudo ./configure
sudo make
sudo make check
sudo make install

  Install WiringPi libraries

sudo dpkg -i wiringpi-latest.deb
gpio -v

  Install Python3 libraries

sudo apt-get update
sudo apt-get install python3-pip
sudo apt-get install python3-pil
sudo apt-get install python3-numpy
sudo pip3 install RPi.GPIO
sudo pip3 install spidev
sudo reboot

Subscribe for APIs
  Open Weather Map https://openweathermap.org/api
  News API https://newsapi.org/
  
Update python files attached with your own API
main_code.py
weather_code.py
news_code.py

Create a folder that will contain icons; saved.txt and python files
mkdir your_filename

add the content of "fonts" folder to the font folder of the RaspberryPi (using WinSCP)
usr/share/fonts/truetype

I have found weather icons from https://www.flaticon.com/ you can choose yours
Create a folder named "icons" in your_filename

run as root
sudo su
python3 main_code.py

Enjoy
