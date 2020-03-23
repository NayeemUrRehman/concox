# Concox
## Run
> ```node adapter.js```

> ```node simulator.js```

## Decoding GPS Packet

### Check 
- Check the protocol number which is the fourth byte if it is `0x22` then the packet contains GPS packet.

### Getting longitude and latitude
- Both latitude and longitude are 4 bytes , so checking the bytes `12-15` and `16-19` converting them to decimal and dividing by `1800000` will give us the latitude and longitude of the device.

### Date and time
- 6 bytes are reserved for date and time . Starting from `year` , `month` , `day` , `hour` , `minute` , `second ` each is assigned 1 byte. Covering them into decimal will give us the date and time.

### Course and Status
- Two  bytes are consumed, defining the running direction of GPS. The value ranges from `0° to 360° ` measured clockwise from north of `0°`

- It is 2 bytes that means we can Convert it to binary number of 16 bits and calculate by its the information.

- first two bits define starting bits which will both set to 0,next four bits give us information of (north latitude, east longitude, GPS positioning and real time gps) last 10 bits give us information about the course and
- Example : the value is 0x15 0x4C, the corresponding binary is `00010101 01001100`, which means GPS tracking is on, real time GPS, location at north latitude, east longitude and the course is  `332°`.