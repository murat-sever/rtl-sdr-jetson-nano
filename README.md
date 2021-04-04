# rtl-sdr-jetson-nano

In order to install driver necessary to access RTL-SDR, follow the steps below, 
`git clone git://git.osmocom.org/rtl-sdr.git`

`cd rtl-sdr/`

`mkdir build`

`cd build`

`cmake ../ -DINSTALL_UDEV_RULES=ON`

`make`

`sudo make install`

`sudo ldconfig`

After that, check that you have access to RTL-SDR using rtl_test utility. 
<pre><font color="#8AE234"><b>murat@jnano</b></font>:<font color="#729FCF"><b>~</b></font>$ rtl_test
Found 1 device(s):
  0:  Realtek, RTL2838UHIDIR, SN: 00000001

Using device 0: Generic RTL2832U OEM
Found Rafael Micro R820T tuner
Supported gain values (29): 0.0 0.9 1.4 2.7 3.7 7.7 8.7 12.5 14.4 15.7 16.6 19.7 20.7 22.9 25.4 28.0 29.7 32.8 33.8 36.4 37.2 38.6 40.2 42.1 43.4 43.9 44.5 48.0 49.6 
[R82XX] PLL not locked!
Sampling at 2048000 S/s.

Info: This tool will continuously read from the device, and report if
samples get lost. If you observe no further output, everything is fine.

Reading samples in async mode...
^CSignal caught, exiting!

User cancel, exiting...
Samples per million lost (minimum): 0
</pre>

You can listen to radio station with rtl_fm utility with a command like
<pre><font color="#8AE234"><b>murat@jnano</b></font>:<font color="#729FCF"><b>~</b></font>$ rtl_fm -M wbfm -g 40 -f 87.5M | aplay  -r 32000 -f S16_LE -c 1
Found 1 device(s):
  0:  Realtek, RTL2838UHIDIR, SN: 00000001

Using device 0: Generic RTL2832U OEM
Found Rafael Micro R820T tuner
Tuner gain set to 40.20 dB.
Tuned to 87771000 Hz.
Oversampling input by: 6x.
Oversampling output by: 1x.
Buffer size: 8.03ms
Exact sample rate is: 1020000.026345 Hz
Playing raw data &apos;stdin&apos; : Signed 16 bit Little Endian, Rate 32000 Hz, Mono
Sampling at 1020000 S/s.
Output at 170000 Hz.
underrun!!! (at least 121,734 ms long)
^CSignal caught, exiting!
Aborted by signal Interrupt...

User cancel, exiting...
Signal caught, exiting!
</pre>
