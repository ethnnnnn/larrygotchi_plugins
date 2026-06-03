# LARRYGOTCHI-torch-plugins

![Larry the Cat, aka Evil Larry, Destroyer of the Universe](https://cdn3.emoji.gg/emojis/21098-larry-evil.png)

my own personal custom plugin repo for all the stuff i either wanna run on larrygotchi or might wanna hang on to just in case

ima try to copy and paste instructions when necessary as well

shout out to all the chronically online unemployed geniuses making these plugins, never change guys <3

---

Edit your `/etc/pwnagotchi/config.toml` to look like this

```TOML
main.custom_plugin_repos = [
    "https://github.com/ethnnnnn/larrygotchi-torch-plugins/archive/master.zip",
    ]
```
Then run this command: `sudo pwnagotchi plugins update`


# Bluetooth-Sniffer
**Warning: This might not work with bt-tether enabled.**

Run the following command to install BtS

`sudo pwnagotchi plugins install bluetoothsniffer`

Add the following lines to your `/etc/pwnagotchi.config.toml`

```TOML
main.plugins.bluetoothsniffer.enabled = true
main.plugins.bluetoothsniffer.timer = 45 # On how may seconds to scan for bluetooth devices
main.plugins.bluetoothsniffer.devices_file = "/root/handshakes/bluetooth_devices.json"  # Path to the JSON file with bluetooth devices
main.plugins.bluetoothsniffer.count_interval = 86400 # On how may seconds to update count bluetooth devices
main.plugins.bluetoothsniffer.bt_x_coord = 160
main.plugins.bluetoothsniffer.bt_y_coord = 66
```

# Internet-Connection
Run the following command to install Internet-Connection

`sudo pwnagotchi plugins install internet-connection`

Add the following line to your `/etc/pwnagotchi/config.toml`

```TOML
main.plugins.internet-connection.enabled = true
```

# Memtemp-Plus
Run the following command to install Memtemp-Plus

`sudo pwnagotchi plugins install memtemp-plus`

Add the following lines to your `/etc/pwnagotchi/config.toml`

```TOML
main.plugins.memtemp-plus.enabled = true
main.plugins.memtemp-plus.scale = "fahrenheit"  # options are celsius, fahrenheit, kelvin
main.plugins.memtemp-plus.orientation = "horizontal"  # options are vertical or horizontal
main.plugins.memtemp-plus.fields = ["mem,cpu,temp"]  # you can change order
main.plugins.memtemp-plus.position = "200,70"
main.plugins.memtemp-plus.linespacing = 12
```

# Show_Pwd
Run the following command to install Show_Pwd

`sudo pwnagotchi plugins install show_pwd`

Add the following lines to your `/etc/pwnagotchi/config.toml`

```TOML
main.plugins.show_pwd.enabled = true
main.plugins.show_pwd.orientation = "horizontal"  # options are horizontal or vertical
```

# GPSdeasy

## There is no reason to reboot during this installation, you may interrupt the apt install that is in the background and this will make your pi go bonk
 
1. install the python file. 
2. find the serial link of your GPS and its baudrate and add them to your config
3. get internet and load the plugin
 
## Example config
### Required, require but if they are not given the values below are defaults
```
main.plugins.gpsdeasy.enabled = true
main.plugins.gpsdeasy.host = '127.0.0.1'
main.plugins.gpsdeasy.port = 2947
main.plugins.gpsdeasy.device = '/dev/ttyS0' #<--- change to your device
main.plugins.gpsdeasy.baud = 9600 #<--- change to fit yuor device
```
### Optional, below values are defaults if not specified
```
main.plugins.gpsdeasy.fields = ['fix','lat','lon','alt','spd'] #<-- Any order or amount, you can also use custom values from POLL.TPV; on gpsd documents (https://gpsd.gitlab.io/gpsd/gpsd_json.html#_tpv)
main.plugins.gpsdeasy.speedUnit = 'kph' #or 'mph' or 'ms' #(m/s)
main.plugins.gpsdeasy.distanceUnit = 'm' #or 'ft'
main.plugins.gpsdeasy.bettercap = true #<--- report to bettercap
main.plugins.gpsdeasy.topleft_x = 130
main.plugins.gpsdeasy.topleft_y = 47
main.plugins.gpsdeasy.auto = true #<--- auto setup systemd service for gpsd. use false if using custom service and you know what you are doing.
```
# Experience-Plugin-Pwnagotchi

A totally not useful plugin for the Pwnagotchi, making it get experience everytime he Associates, Deauths or get a Handshake. Try to level him up!

![EXP Plugin](exp_new.jpg)

Wanted to make him more like a Tamagotchi, but moved that idea on another project.

I'm a total newb when it comes to Python so, feel free to help if you see im doing some bad stuff, or you've got some interesting ideas.

Thanks to @mbudget0x01 and @hannadiamond for all the cool stuff!

## Setup
1. Copy over `exp.py` into your custom plugins directory
2. In your `config.toml` file, add:
```toml
   main.plugins.exp.enabled = true
   main.plugins.exp.lvl_x_coord = 0
   main.plugins.exp.lvl_y_coord = 81
   main.plugins.exp.exp_x_coord = 38
   main.plugins.exp.exp_y_coord = 81
   main.plugins.exp.bar_symbols_count = 12
```
3. Restart your device to see your new plugin!


## Things to do
  
- [x] Better Save System -> Saves are now in json Format and will per default migrate.
  
- [x] Make him count how many Handshake you have already captured and try to make a fair level up if you're not starting from zero, and you just installed the plugin [Example: if i already have 250 Handshake when i start the plugin for the first time, my Pwnagotchi will only be lv 1, while it should be lv 13(?)] -> if session-stats Plugin is installed, initially the data will be parsed from there. If not, just the last session will be counted.

- [x] Make Things configurable through settings.

- [ ] Testing, lots of testing.

# Age Plugin
A plugin that adds age and int stats based on the the time training and the number of epochs trained.
Whenever your pwnagotchi has lived through another 100 epochs or epochs trained, a new status will appear!
 ![Age](images/age.jpg)

## Setup
1. Copy over `age.py` into your custom plugins directory
2. In your `config.toml` file add:
```toml
main.plugins.age.enabled = true
main.plugins.age.age_x_coord = 0
main.plugins.age.age_y_coord = 32
main.plugins.age.int_x_coord = 67
main.plugins.age.int_y_coord = 32
```
3. Restart your device to see your new stats!
