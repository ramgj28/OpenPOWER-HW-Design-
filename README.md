# AES-128 Accelerator for Microwatt

This project proposes building an AES-128 encryption/decryption unit as a hardware peripheral for
the Microwatt OpenPOWER CPU. AES is the standard block cipher for secure data, and handling it in
hardware reduces CPU overhead while improving performance on small systems. The design will be
kept simple and clear in VHDL, tested against NIST AES vectors, and connected to Microwatt using a
memory-mapped register interface.


### Objectives

1. Build AES-128 block cipher core (encryption and decryption).
2. Expose the core as a Wishbone peripheral with key, input, and output registers.
3. Implement AES key expansion in hardware.
4. Provide status and interrupt signals to software.
5. Test using GHDL and official AES vectors as references.
6. Prepare design for ASIC flow on SKY130 using OpenLane.

### Design Approach

1. Datapath: Implements AES round operations (SubBytes, ShiftRows, MixColumns, AddRoundKey).
2. FSM: Steps through the 10 AES rounds.
3. Key Expansion: Generates round keys from the 128-bit key.
4. Registers: Memory-mapped for key, input, and output blocks.
5. Interrupt: One line raised when encryption/decryption is complete.

### Work Plan

Build peripheral skeleton, bus interface, and FSM.
Implement AES round operations and integrate into FSM.
Add key expansion and decryption. Verify using NIST vectors.
Integrate with Microwatt, refine testing, run synthesis, and prepare demo.

### Expected Outcome
The outcome will be a compact AES-128 hardware accelerator that works with Microwatt as a
memory-mapped peripheral. It shows how hardware offload can improve cryptography performance
while serving as an educational reference for cryptographic hardware design.
