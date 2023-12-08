# digiplant

Create a digital twin of a plant that take cares of the real twin :)

**Disclaimer**: This is a small side project mainly created to give as prize in the sdsc-hackathons, genAI 2023 by SDSC. Also it still requires to be polished a little bit, so if you want to give a hand please feel free to do a PR. 

## v.0.0.1 

This version creates a systems that detect when your plant is needing some water and activate a pump to save it.

### What do you need?

- Plant
- Water recipient
- [BBC micro:bit v2](https://www.adafruit.com/product/4781)
- [Plant Care Kit for micro:bit or CLUE](https://www.adafruit.com/product/4746)

### Steps?

You can find detailed instructions [here](https://learn.adafruit.com/adafruit-bonsai-buckaroo)

1. Connect the Bonsai board to the Micro:bit.
2. Wire the pump and the crocodriles pins to the Bonsai board.
3. Connent the micro:bit to your computer. 
4. Go to [python.microbit.org](https://python.microbit.org/v/3)
5. Connect to the board. 
6. Write this code:

```
from microbit import *

def read_and_average(analog_in, times, wait):
    analog_sum = 0
    for _ in range(times):
        analog_sum += analog_in
        sleep(wait)
    return analog_sum / times

while True:
    # Take 100 readings and average them
    analog_value = read_and_average(pin1.read_analog(), 100, 0.01)
    # Calculate a percentage (analog_value ranges from 0 to 1024 )
    percentage = analog_value / 1024  * 100
    # Display the percentage
    display.show("S: {} %".format(int(percentage)))
    # Print the values to the serial console
    print((analog_value, percentage))

    if percentage < 50:
      pass
      #TODO: Motor on

```

7. Check that the pump is activated when you put the pins close or far away.
