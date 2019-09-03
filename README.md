# Blinky app for the Tiva C Series Launchpad

A blinky app for the [Tiva C Series Launchpad (EK-TM4C123GXL)](http://www.ti.com/ww/en/launchpad/launchpads-connected-ek-tm4c123gxl.html). When loaded and run the Launchpad LED flashes -- switching between red, green and blue.

The project source is in **src**. The main loop in main.c drives the application.

There are two software modules -- **state** and **led** -- used to determine the LED color (the state) and to set the color of the LED. Each of these modules implements units tests. Unit tests are in **test**.

In the **led** module, the TivaWare Peripheral Driver Library is used to initialize and control the GPIO pins connected the multi-color LED. This library is in **lib/TivaWare/driverlib** and is built automatically if necessary.

## Building and loading

Execute all unit tests with `ceedling test:all`.

Run a single test with `ceedling test:<module>`, e.g. `ceedling test:led`.

Build the application for the target with: `ceedling release`.

Load the app on the board with: `ceedling load`. The load command also builds the application if necessary.
