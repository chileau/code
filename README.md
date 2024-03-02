Abstract

An ultrasonic rangefinder, a device that can determine the distance between an
object and the device through ultrasonic waves, has a range of up to 4 meters with an
accuracy of 1 cm. The device is composed of two main components: the AT89S52
microcontroller and the ultrasonic transducer module HC-SR04. When the
ultrasonic module sends a signal to the object, it picks up its echo and outputs a
waveform whose time period is proportional to the distance. This signal is then
accepted by the microcontroller which performs necessary processing and displays
the corresponding distance on the LCD display.
Due to the versatility of this circuit, it finds many applications in various projects
including but not limited to automotive parking sensors, obstacle warning systems,
terrain monitoring robots, and industrial distance measurements. The device has
been used in the automotive industry for many years, particularly in parking sensors
to help drivers park their vehicles safely. Moreover, the device can also be used in
obstacle warning systems to alert drivers of potential dangers ahead. In addition,
terrain monitoring robots can use ultrasonic rangefinders to navigate through rough
terrain and avoid obstacles. The device is also used in industrial distance
measurements to accurately determine the distance between two objects. The device
can also be modified to be used to detect moving objects (such as cars racing on the
street) and find their range and speed, enabling the detection of traffic violations.

Table of Contents
1. Introduction

   1.1. Objective
   
   1.2. Deliverables
   
2. Product Specifications
3. Block Diagram

   3.1. Components Required
   
4. Circuit Diagram
5. Working
6. Code
7. Results
8. Conclusion
9. Future Scope
10. References

Introduction

1. Objective:
To build an Ultrasonic Rangefinder using an 8051 Microcontroller and Ultrasonic Sensor which measures distances up to 4 meters.



2. Deliverables:

   2.1 Hardware Requirements:
   
     2.1.1 8051 Microcontroller - AT89S52
   
     2.1.2 HC-SR04 Ultrasonic Sensor
   
     2.1.3 16x2 LCD Display Unit
   
     2.1.4 10K Potentiometer
   
     2.1.5 Jumper Wires
   
   2.2 Software Requirements:
   
     2.2.1 Keil Uvision 3
   
     2.2.2 Programming Language: C language

Product Specifications

  1. Input voltage: 5 V DC
     
  3. Static current: <2 mA
     
  5. Output voltage: 5 V high and 0 V low
     
  7. Detection range: 2 cm to 400 cm
     
  9. Dimensions: 25 x 16 x 6.5 cm
      
  11. Input trigger signal: 10 μs TTL impulse
      
  13. Echo signal: output TTL PWM signal

Components Required

The major components in this project are AT89C51 Microcontroller, Ultrasonic
Sensor and LCD Display. The TRIGGER and ECHO pins of the Ultrasonic Sensor are
connected to the P3.2 and P3.5 pins respectively. LCD data pins are connected to the
PORT2 of the microcontroller and controller pins RS, RW and EN are connected to
the P0.0, P0.1and P0.2 respectively. Here, the LCD (Liquid Crystal Display) is used
to display the distance of the object. 10KΩ POT is used to vary the contrast of the
LCD. The power supply pins of the microcontroller, LCD and Ultrasonic Sensor are
connected to the 5V DC.

HC-SR04 Ultrasonic Module:

HC-SR04 is an ultrasonic ranging module designed for embedded system projects
like this. It has a resolution of 0.3cm and the ranging distance is from 2cm to 500cm.
It operates from a 5V DC supply and the standby current is less than 2mA. The
module transmits an ultrasonic signal, picks up its echo, measures the time elapsed
between the two events and outputs a waveform whose high time is modulated by the
measured time which is proportional to the distance.
The supporting circuits fabricated on the module make it almost stand alone and
what the programmer needs to do is to send a trigger signal to it for initiating
transmission and receive the echo signal from it for distance calculation. The
HR-SR04 has four pins namely Vcc, Trigger, Echo, and GND and they are explained
in detail below.

1) VCC: 5V DC supply voltage is connected to this pin.

2) Trigger: The trigger signal for starting the transmission is given to this pin. The
trigger signal must be a pulse with 10uS high time. When the module receives a valid
7 trigger signal it issues 8 pulses of 40KHz ultrasonic sound from the transmitter. The
echo of this sound is picked up by the receiver.

3) Echo: At this pin, the module outputs a waveform with high time proportional to
the distance.

4) GND: Ground is connected to this pin.The cycle period for HC-SR04 must not be below 50 mS. According to the datasheet,
the distance can be calculated from the echo pulse width using the following
equations.

8051 Microcontroller:

A microcontroller is a highly integrated chip or a microprocessor with all peripherals
like RAM, ROM, I/O ports, Timers ADC etc. on a single chip. It is a dedicated chip
called a single-chip computer.
The 8051 microcontroller is a popular 8-bit microcontroller. It is based on the 8-bit CISC
core of Harvard architecture. It is available as a 40-pin DIP pin chip and works with
5volts DC input. The 8051 microcontroller is available in 40 pin DIP configuration.
Among 40 pins, 32 pins are allotted for four parallel ports P0, P1, P2 and P3, each
port occupying 8 pins. The remaining pins are VCC, GND, XTAL1, XTAL2, RST, EA
and PSEN. A quartz crystal oscillator is connected across the pins XTAL1 and XTAL2
with a capacitor value of 30pF. If a source other than a crystal oscillator is used, the pins XTAL1 and XTAL2 are left open. The 8051 microcontroller has two pins for
transferring and receiving data through serial communication. These two pins are
part of port P3 (P3.0 and P3.1). These pins are TTL compatible and hence they
require a line driver to make them RS232 compatible. MAX232 is used as a line
driver. Serial communication is controlled by an 8-bit register called the SCON
register.

Features of 8051 Microcontroller

● 4KB on-chip program memory (ROM and EPROM).

● 128 bytes on-chip data memory (RAM).

● The 8-bit data bus, 16-bit address bit and two 16-bit timers T0 and T1

● 32 general-purpose registers each of 8 bits and five interrupts.

● Four parallel ports each of 8 bits with 32 I/O lines.

● One 16-bit program counter, one stack pointer and one 16-bit data pointer.

● One-microsecond instruction cycle with 12 MHz crystal.

● One dull duplex serial communication port

Working

1. The HC-SR04 module has an ultrasonic transmitter, receiver and control circuit
on a single board. The module has only 4 pins, Vcc, Gnd, Trig and Echo.

3. When a pulse of 10sec or more is given to the Trig pin, 8 pulses of 40 kHz are
generated.
After this, the Echo pin is made high by the control circuit in the module.

5. The echo pin remains high till it gets the echo signal of the transmitted pulses back.
   
7. The time for which the echo pin remains high, i.e. the width of the Echo pin
gives the time taken for generated ultrasonic sound to travel towards the
object and return.

9. Using this time and the speed of sound in air, we can find the object's distance using a simple formula for distance using speed and time.

To measure distance

Object Distance(in cm) = (Sound Velocity * Time)/2,

Where, Sound Velocity = 34300 (in cm per second)

Here, oscillator frequency of AT89S52 (8051) is 11.0592 MHz, then timer frequency
of 8051 will be 921.6 kHz.

So, Time required to execute 1 instruction is 1.085 µs.

So, timer gets incremented after 1.085 µs time elapse.

Hence, 

    Distance = (34300 * 𝑇𝑖𝑚𝑒𝑟𝐶𝑜𝑢𝑛𝑡 * 1.085 * 10−6) / 2
             = 𝑇𝑖𝑚𝑒𝑟𝐶𝑜𝑢𝑛𝑡 / 54

Conclusion

Hence, we can conclude that the device can be used to find the distance of an object
from a point accurately within a short range.

The ultrasonic ranger satisfied the following specifications:

● Distance measurement after beam reflection and displaying on LCD using an
ultrasonic beam of about 40 KHz.

● Resolution of 1 cm.

▪ Range limit:

▪ Minimum = 1 cm

▪ Maximum = 3 m.



Future Scope

The following improvements can be added to the module described to get an
improved throughput.

● Temperature Calibration Feature:

It is well known that the speed of sound changes with temperature. At 0°C, it is
331.5m/sec. At 40°C, it is 355.5m/sec. In our module, while measuring distance, we
assumed that the speed of sound in air is 343 m/sec, which stands only at 27°C. The
distance measured will not be accurate if the temperature is different during the
measurement. This drawback can be rectified by including a temperature-measuring
circuitry in the module and adjusting the calculations for distance measurement
accordingly.

● Range Improvement:

When the time of generation of the pulse increases, the energy of the ultrasonic
increases, enabling the long-range measurement. However, when making a
transmission pulse long, the signal which influences a receiver increases. Therefore,
the guard time must be made long and it becomes impossible to measure distances in
short range. The shortest measurement distance is decided by the total value of
guard time and the pulse sending-out time.

References

● https://en.wikibooks.org/wiki/Embedded_Systems/8051_Microcontroller

● https://www.elprocus.com/8051-microcontroller-architecture-and-applications/

● http://wiki.sunfounder.cc/index.php?title=Ultrasonic_Module

● https://dxarts.washington.edu/wiki/hc-sr04-ultrasonic-rangefinder

● https://wiki.52pi.com/index.php/D-0013

● https://web.cecs.pdx.edu/~gerry/class/IB/sensors/HC-SR04/#:~:text=Vendor%20Information-,Physical%20Operating%20Principle,the%20arrival%20of%20its%20echo

● https://circuitdigest.com/microcontroller-projects/lcd-interfacing-with-8051-microcontroller-89s52

● https://www.watelectronics.com/lcd-16x2/
