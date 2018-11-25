this repo explains howto setup SWD (serial wire debug) on a orange pi

My intention was to connect a nrf51 (id107 smartwatch) to an orange pi without using a dongle.

After searching the net : 

(first you have to setup the GPIO)
- first install WiringOP https://github.com/zhaolei/WiringOP


(adapt openocd)
- https://github.com/bhgv/openocd

I used the modified files and put them in the most recent version of openocd 

then I used my_configure.sh (script) to configure openocd

(followed by make and make install)


to wire the nrf51 smartwatch, connect clk to pin 12 and dio to pin 10 (see file wiring)


to start openocd for the nrf51 microcontroller: (see startdebugger script)


openocd -f  /usr/local/share/openocd/scripts/interface/sysfsgpio-raspberrypi.cfg -c 'transport select swd'   -f /usr/local/share/openocd/scripts/target/nrf51.cfg -c 'bindto 0.0.0.0'


this starts the session to which you can connect : with : telnet 127.0.0.1 4444



