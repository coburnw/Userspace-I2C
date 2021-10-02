# Userspace-I2C
A Linux userspace I2C class in C++

The goal is to have an I2C utility library that can be dropped into a Linux project that is intuitive,
simple, and effective.

For example:
```
uint8_t bus_id = 1;
uint8_t chip_addr = 0x60;
uint8_t reg_addr = 0;

I2C i2c = I2C(bus_id, chip_addr);

int data = i2c.read_byte(reg_addr);
if (data < 0)
   handle_error();
else
   cout << std::to_string(data)
```
When run on a raspberry pi zero, the above example would open /dev/i2c-1 configuring the file descriptor to interact 
with the device at bus address 0x60, then read a single byte from register 0.

Note the makefile is for building a .so library that could be installed.  As i use the source dropped 
directly into my projects source tree, this functionality has not been tested.
