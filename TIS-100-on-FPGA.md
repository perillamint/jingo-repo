# Design
## Nodes
### T-20
* Reserved node
* ~~Not implemented in game?~~
* TIS-NET directory has spec about it.
* Same as T-21 but BAK is directly accessible using MOV

### T-21
* Basic Execution node

#### Architecture
* Three internal regs - ACC, BAK, NIL
* ACC can directly accessed.
* BAK cannot be directly accessed.
* NIL - read produces zero, Writing does not has effect.

* I/O regs - LEFT, RIGHT, UP, DOWN, ANY, LAST
* LEFT, RIGHT, UP, DOWN - Interface with other nodes.
* ANY - Send/Recv data to/from first available node.
    * Priority - LEFT RIGHT UP DOWN
* LAST - Last direction used by using ANY reg.

#### Instruction set
* NOP - does nothing
* MOV SRC DST - Read value from SRC and write it to DST
* SWP - Swap ACC and BAK
* SAV - Write BAK with value of ACC
* ADD SRC - Add SRC to ACC
* SUB SRC - Sub SRC from ACC
* NEG - Value of ACC is negated.
* JMP ADDR - Jump to address. (Originally, it was a label)
* JEZ ADDR - Jump to address if ACC is zero.
* JNZ ADDR - Jump to address if ACC is not zero.
* JGZ ADDR - Jump to address if ACC is greater then zero.
* JLZ ADDR - Jump to address if ACC is lesser then zero.
* JRO SRC - Jump to address PC + SRC * (word size)

#### Timing
* Single-cycle
* MOV can take two or more cycle when communicating using port

#### Design
##### Objective
Implement TIS-100 with some enhancement which may simplify design.

##### Register
Register width: 16-bit

##### Opcode format
TODO: Do opcode design.

### T-30
* Stack Memory node

### T-31
* Random Access Memory node
* ~~Not yet implemented in game.~~
* TIS-NET directory has spec about it.
* It reads cmd and do operations.
  * CMD 0 reads additional two args.
    * First arg is idx.
    * Second arg is data.
    * It stores data on idx.
  * CMD 1 reads additional one arg.
    * Arg is idx.
    * It reads value at idx and return that value.

# Used resources
* Target board - Lattice iCE40-HX8K breakout board
* Toolchain - iCEstorm open-source toolchain