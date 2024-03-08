## Preliminary Analysis on the provided 'Shelly' binary

#### Running Checksec and File on the given binary

![1709890282094](image/ShellyWriteup/1709890282094.png)

- The binary has all protections disabled
  - **NX Disabled**
    - Stands for No-Execute i.e. the data section of the binary is marked as non-executeable when this bit is on but when off we can send shellcode to be stored and executed from variables that are populated via stdin functions
  - **Partial RELRO aka Relocation ReadOnly**
    - Understanding RELRO is a little confusing as it deals with 2 main concepts
      - Global Offset Table
        - This is used to dynamically resolve the functions located in shared libs
      - Procedure Linkage Table
        - Contains the x86 instructions that point directly to the GOT
      - When partial, the GOT is read-only but the PLT can be modified which is the case in the provided binary
  - **No PIE (Position-Independent Code)**
    - This means that the locations where the binary and its dependencies are loaded into memory are always randomized. When disabled and used along with a kernel that has no ASLR (Address Space Layout Randomization). We can safely use the stack and memory function offsets we calculate during dynamic analysis
  - **No stack canaries**
    - Canaries are used to monitor the stack for buffer overflows

## Observing the vuln function

- Performing static analysis via your reverser of choice i.e ghidra/IDA/GDB we can obeserve a format-string vuln in the printf statement inside the vuln function
- 

## Using GDB and GEF

## Finding the stack offset to print

## Crafting a pwntools script with payload

## Result
