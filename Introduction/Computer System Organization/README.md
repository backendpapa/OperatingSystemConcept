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

**Question**

How does a D.C inform the D.D thats its done executing?

ANS: *Interupt*




## Not Well Understood Concepts
1. The CPU and the device controllers can execute in parallel, competing for memory cycles. To ensure orderly access to the shared memory, a memory controller synchronizes access to the memory.

