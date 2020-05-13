# iot-examples

### Lesson 4

#### Publish a message
- `mosquitto_pub -h test.mosquitto.org -p 1883 -t polimi/iot/2020/lesson4 -m "exercise 1"`
- `-d` for additional information

#### Subscribe to a topic
- `mosquitto_sub -h test.mosquitto.org -p 1883 -t polimi/iot/2020/lesson4`
- `-d -v` for additional information

#### Wildcards
##### Single level (+)
Topic: `polimi/iot/+/lesson4`

- polimi/iot/2020/lesson4 ?
- polimi/iot/2019/lesson4 ?
- polimi/iot/lesson4 ?
- polimi/iot/2020/May/lesson4 ?

##### Multi level (#)
Topic: `polimi/iot/#`

- polimi/iot/2020/lesson4/ ?
- polimi/iot/2021/lesson5/exercise1 ?
- polimi/iot/ ?
- polimi/iot/#/lesson4 ?

- `polimi/iot/#` vs `polimi/iot/+`

#### Start a local broker
`mosquitto -v`

#### Retain message
- `-r`

#### Last Will ex
- Install python3: `sudo apt-get install python3-pip`
- Install paho mqtt package: `python3 -m pip install paho-mqtt`
- Start a subscriber: `mosquitto_sub -t <hostname> -t <topic>`
- Run `python3 last_will.py` and kill it

- Non working will message: `mosquitto_pub -h localhost -t room2/bulb -m ON --will-payload "error, bulb disconnected" --will-topic room2/bulb/error --will-qos 2`

#### $SYS topics
- `mosquitto_sub -h test.mosquitto.org -t "\$SYS/broker/clients/connected"`
