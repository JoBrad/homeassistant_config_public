# Configuration with HomeAssistant
Instructions are taken from https://www.homeautomationguy.io/docker-tips/configuring-the-mosquitto-mqtt-docker-container-for-use-with-home-assistant/

## Create password file entry

NOTE: To persist this config, make sure you have started the MQTT container using a local directory as the config volume. 

Run this command in the MQTT container to create a new MQTT user and password for authentication.

```
mosquitto_passwd -c /mosquitto/config/password.txt hass
```

This uses the `mosquitto_password` command to create (the `-c` switch) a new user in the `/mosquitto/config/password.txt` file with a username of `hass`. You will be prompted to enter a password, and confirm it. Be sure to save this password in your password manager! This will be the password for the `hass` user.

Now set these entries in the mosquitto.conf file:

```
allow_anonymous false
password_file /mosquitto/config/password.txt
```
