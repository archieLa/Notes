# Creational patterns
## Benefits
- encapsulate knowledge about which concrete classes system uses
- hide how instances of these classes are created and put together
- instruct how to make design more flexible but not necessary smaller
## Abstract factory
Exposes interface for creating dependent objects without specifying concrete classes
### Aplicability
- when system needs to be configure with family of objects e.g. family of drivers or widgets
- when there is direct dependencies between objects of the family and they have to be used as a group
- you want to hide implementations of library of products and expose interface only
### Diagram
![abstractFactory image](uml/AbstractFactory.png?)
### Code Example
Factories
```cpp
class DriverFactory
{
    public:
        LcdDriver* create_lcd_driver() = 0 ;
        AccDriver* create_acc_driver() = 0;   
}

class SpiDriverFactory
{
    public:
        LcdDriver* create_lcd_driver()
        {return new LcdSpiDriver();}
        AccDriver* create_acc_driver()
        {return new AccSpiDriver();}
}

class I2CDriverFactory
{
    public:
        LcdDriver* create_lcd_driver()
        {return new LcdI2cDriver();}
        AccDriver* create_acc_driver()
        {return new AccI2cDrive();}
}
```
Drivers
```cpp
class LcdDriver
{
    public: 
        void display_msg() = 0;
}

class AccDriver
{
    public:
        void read_acc_data() = 0;
}

class LcdSpiDriver : public LcdDriver
{
    public:
        void display_msg() {}
}

class AccSpiDriver : public AccDriver
{
    public:
        void display_msg() {}
}

class LcdI2cDriver : public LcdDriver
{
    public:
        void display_msg() {}
}

class AccI2cDriver : public AccDriver
{
    public:
        void display_msg() {}
}
```
Usage example
```cpp
DriverFactory* driversCreator;

if (config == "spi")
{
    driversCreator = new SpiDriverFactory; 
}
else if (config == "i2c")
{
    driversCreator = new I2cDriverFactory;
}

LcdDriver* lcdDriver = driversCreator->create_lcd_driver();
AccDriver* accDriver = driversCreator->create_acc_driver();
```








