## Computer System Organization

```javascript
{ "Common Bus": "A pair of signal lines that facilitate the transfer of multi-bit data from one system to another" }


{"Shared Memory": "Memory that may be simultaneously accessed by multiple programs with an intent to provide communication among them or avoid redundant copies"}


{"Local Storage Buffer": "Stored input and output data from / to device"}


{"Speical Register Set": "A register that hold and manages a special microprocessor function"}
```

- A device controller controls a specific device. Examples of devices such as disk drive, audio device, USB device.



- Device controllers maintain their own ```local storage buffer``` and a ```special set of registers```


**Device Controllers(D.C)** is responsible for moving data between a device(peripheral) and its local buffer storage.

**Device Driver** understands the device controller and allows interaction beteern the D.C and the O.S

### Interrupts

#### IO Operation flow
1. Device driver loads appropriate registers associated with the device controller
2. The Device controller reads the content of the register to determine what action to carry out.
3. The D.C starts transfer of data from the device to its local buffer storage
4. Informs the D.D of completed execution
5. D.D transfers control back to the system.

EXIT

**Question**

How does a D.C inform the D.D thats its done executing?

ANS: *Interupt*


- Hardware trigger interrupts by sending signals to the CPU via system bus.

#### CPU Interrupt Response Flow
1. When CPU is interrupted
2. Stop current executions and transfer control or execution to the interrupt address which contains the ISR( Interrupt Service Routine). ISR determines how to handle the interrupt.
3. Once ISR completes execution, control is handed back and CPU resumes interrupted execution

EXIT

- Table of pointers hold the addresses of the ISR of various devices
- The interrupt must save the state of the interrupted service so it can restore after completed execution.

#### Interrupt Implementation
1. D.C hits a IRL (Interrupt Request Line)
2. CPU detects this signal and read the interrupt number from the signal
3. CPU uses this interrupt number to index the arrays in the Interrupt Vector and jump to the signalling ISR.

EXIT

#### Roles of Interrupt Service Routine
1. Saves interrupted state
2. Checks possible cause of interrupt
3. Performs executions
4. Performs state restore
5. executes a ```return_from_interrupt``` instruction to return control to CPU to continue its prior execution before the interrupt.

EXIT

#### System Interrupt Flow
- D.C ```raises``` an interrupt and assert a signal on the IRL
- CPU ```catches``` the signal and ```dispatches``` the Interupt number to the ISR
- ISR ```clears``` the interrupt.

EXIT

- CPU have two IRL :
  1. Unmaskable IRL: Cannot be controlled by the CPU, examples such as system failure. (VECTOR 0-31)
  2. Maskable IRL: Can be turned off by the CPU expecially when the CPU is working on a critical execution that must not be interrupted, this is the IRL D.C uses. (VECTOR 32-255) 


### Storage structure
- CPU loads instruction from memory(RAM), a semiconductor.
- RAM cant be used to store boot program because it is volatile.
- A memory is an array of bytes(4 bits)
- Each byte has its own memory address
- CPU ```load``` a byte from the memory or ```store``` a data into the meomry from the register

#### Differences between Main Memory and Secondary Memory

<table>
<tr>
<td></td>
<td>Main Memory</td>
<td>Secondary Memory</td>
</tr>

<tr>
<td>1</td>
<td>Volatile</td>
<td>Non volative</td>
</tr>
<tr>
<td>2</td>
<td>Expensive</td>
<td>Cheap</td>
</tr>
<tr>
<td>3</td>
<td>Smaller size</td>
<td>Larger size</td>
</tr>
<tr>
<td>4</td>
<td>Faster</td>
<td>Slower</td>
</tr>
</table>
NB: There are two types of storage

1. Mechanical storage(such as HDD)
2. Electrical storage(such as SSD)

## Not Well Understood Concepts
1. The CPU and the device controllers can execute in parallel, competing for memory cycles. To ensure orderly access to the shared memory, a memory controller synchronizes access to the memory.



