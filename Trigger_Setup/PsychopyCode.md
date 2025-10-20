# BIOPAC Serial Port Triggers

This guide describes the hex codes for each BIOPAC channel setting and how to send triggers via a serial port in Python (e.g., for PsychoPy experiments).

---

## Hex Codes for Channels

| Hex Code | BIOPAC Channels |
|----------|----------------|
| `00`     | All closed     |
| `04`     | Channel 20     |
| `02`     | Channel 22     |
| `01`     | Channel 23     |
| `08`     | Channel 27     |
| `03`     | Channels 22 + 23 |
| `06`     | Channels 20 + 22 |
| `0C`     | Channels 20 + 27 |
| `07`     | Channels 20, 22 + 23 |
| `0E`     | Channels 20, 22 + 27 |
| `0D`     | Channels 20, 23, 27 |
| `0F`     | Channels 20, 22, 23 + 27 |
| `RR`     | Reset port     |

---

## Setting Up the Serial Port

Insert the following at the beginning of your experiment code:

```python
import serial

# Configure serial port (customize COM port as needed)
ser = serial.Serial("COM3", 115200, timeout=1, bytesize=8, stopbits=1)

# Open the port and reset
ser.open()
ser.write('RR'.encode())  # Reset port to prepare for first trigger
```
## Sending a Trigger

### Sending at a fixed point:

```python
# Turn on BIOPAC channel 27
ser.write('08'.encode('utf-8'))
core.wait(0.005)  # Wait for .005 seconds before closing the trigger.
# Turn off all channels
ser.write('00'.encode('utf-8'))
# Reset port after sending
ser.write('RR'.encode('utf-8'))
```

> **Note:**  
> <details>
> <summary>Click to expand</summary>
> The duration of core.wait() can be adapted to match the settings in BIOPAC that determine what the minimum amount of time a trigger must be open for inorder for it to be recognised as a digital stim event.
> </details>



### Sending a Trigger When a Stimulus Begins Alternatively(Psychopy Builder)

Begin Routine Tab

```python
stimulus_pulse_started = False
stimulus_pulse_ended = False
```

Each Frame Tab

```python
if stimulus.status == STARTED and not stimulus_pulse_started:
    # Change 'stimulus' to match your component
    win.callOnFlip(ser.write, str.encode('03'))
    stimulus_pulse_start_time = globalClock.getTime()
    stimulus_pulse_started = True

if stimulus_pulse_started and not stimulus_pulse_ended:
    if globalClock.getTime() - stimulus_pulse_start_time >= 0.005:
        win.callOnFlip(ser.write, str.encode('00'))
        stimulus_pulse_ended = True
```

End Routine Tab

```python
ser.write ('RR'.encode('utf-8'))
```

At the end of your experiment, ensure you close the port
```python
ser.close
```
