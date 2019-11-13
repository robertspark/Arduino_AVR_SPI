# Arduino AVR SPI
This library allows you to communicate with SPI devices, with the Arduino as the master device.
[SPI Library](https://www.arduino.cc/en/Reference/SPI)

## Usage
Provided for [XOD.io](https://xod.io/) library import
`#pragma XOD require "https://github.com/robertspark/Arduino_AVR_SPI"`

Include the library:
`#include <spi.h>`

**Macro definitions:**
* `SPISettings mySettting(speedMaximum, dataOrder, dataMode)` used to configure the SPI port for your SPI device 
* `begin()` Initializes the SPI bus by setting SCK, MOSI, and SS to outputs, pulling SCK and MOSI low, and SS high
* `end()` Disables the SPI bus (leaving pin modes unchanged).
* `beginTransaction()` Initializes the SPI bus using the defined SPISettings.
* `endTransaction(mySettings)` Stop using the SPI bus. Normally this is called after de-asserting the chip select, to allow other libraries to use the SPI bus.
* `transfer(val)`
* `transfer16(val16)`
* `transfer(buffer, size)`
SPI transfer is based on a simultaneous send and receive: the received data is returned in receivedVal (or receivedVal16). In case of buffer transfers the received data is stored in the buffer in-place (the old data is replaced with the data received).
* `usingInterrupt(interruptNumber)` 
If your program will perform SPI transactions within an interrupt, call this function to register the interrupt number or name with the SPI library. This allows SPI.beginTransaction() to prevent usage conflicts. Note that the interrupt specified in the call to usingInterrupt() will be disabled on a call to beginTransaction() and re-enabled in endTransaction().

**Parameters:**
* `speedMaximum` - The maximum speed of communication. For a SPI chip rated up to 20 MHz, use `20000000`
* `dataOrder` - `MSBFIRST` or `LSBFIRST`
* `dataMode` - `SPI_MODE0`, `SPI_MODE1`, `SPI_MODE2`, or `SPI_MODE3`
* `mySettings` - the chosen settings according to SPISettings
* `val` - the byte to send out over the bus
* `val16` - the two bytes variable to send out over the bus
* `buffer` - the array of data to be transferred
* `interruptNumber` - the associated interrupt number

## Reference
Copied from Arduino IDE 1.8.10

