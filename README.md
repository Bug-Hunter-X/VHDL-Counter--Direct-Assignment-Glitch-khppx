# VHDL Counter with Direct Assignment Issue

This repository demonstrates a subtle bug in a VHDL counter design. The bug relates to directly assigning an internal signal to an output port without proper synchronization, which can lead to unexpected glitches or incorrect output values. 

## The Bug
The `buggy_counter.vhd` file contains the problematic code. The issue lies in the direct assignment:
```vhdl
count <= internal_count;
```
This assignment doesn't consider the timing of signal updates and can result in the output `count` reflecting intermediate or inconsistent values.

## The Solution
The `fixed_counter.vhd` file provides a corrected version. This uses a properly synchronized assignment within the process to ensure reliable output. The update is done in the same process as the counter logic.

## How to Reproduce
1.  Simulate `buggy_counter.vhd` using a VHDL simulator.
2. Observe the behavior of the `count` signal. You might see glitches or unpredictable values depending on the simulation timing resolution.
3. Simulate `fixed_counter.vhd` for comparison. The corrected version should produce the expected sequential counter behavior.

## Conclusion
This example highlights the importance of proper signal assignments and synchronization in VHDL, especially when dealing with outputs that need consistent and predictable values.