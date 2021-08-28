# Ratified extensions of the unprivilaged spec
- M - Integer Multiplication and Division
- A - Atomic Instructions
- F - Single Precision Floating Point Ops
- D - Double Precision Floating Point Ops
- Q - Quad Precision Floating Point Ops
- Ziscr - Control and Status Registers (CSR)
- Zifencei - Instruction-Fetch Fence
- C - Compressed Instructions

# Unratified extensions of the unprevilaged spec
- B - Bit manipulation
- V - Vector Operations
- N - User-level interrupts
- S - Supervisor Level interrupts

# Immidiate encodings: Why are they the way they are?

-- RISC V instructions follow the little endian format and use fixed offsets for important fields so as to be able to easily decode them.

-- Coming to the point, not every instruction type (R, I, S, B, U, J) has the exact same fields in the exact same positions, and more complex instructions might require other calculations to be done, the primary motive is to make the hardware implementation simpler rather than to make it easy to read.

-- Besides, we only require the major opcode (0-6) to know how to decode the immidiate using multiplexars while decoding the rest of the instruction.

-- Answering to the point: The "shuffling" of immidiate bits in the instruction encoding is to make each output immidiate bit have as little to tell to the multiplexar as possible (input instruction bit).

-- https://stackoverflow.com/questions/39427092/risc-v-immediate-encoding-variants was used as a reference to answer this question.

# Custom instructions in the 32bit instruction format, how many of them can we add?

-- RV32 requires a 2 bit offset in each octet for the prefix? so would that mean the other 24 bits are left to me?

That way, we can have a total of 16777215 instructions
If only the opcode can be changed (0-6) and the fiest bit is fixed to 0, then we have 5 bits to play with.

So for R, we would have a headspace of 31 more instructions?
