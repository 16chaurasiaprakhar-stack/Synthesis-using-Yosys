# Synthesis-using-Yosys
This repository demonstrates RTL design and synthesis using the open-source Yosys toolchain. All designs are written in Verilog, verified with testbenches, and synthesized to gate-level netlists using standard cell libraries (osu018).

               
> 
## Yosys Synthesis Flow

```bash
yosys

read_verilog alu16bit.v

hierarchy -check -top alu16bit

proc,opt,fsm,opt,memory,opt

techmap,opt

dfflibmap -liberty osu018_stdcells.lib

abc -liberty osu018_stdcells.lib

clean

write_verilog alu16bit_synth.v

gvim alu16bit_synth.v

show -format dot -prefix my_design_
```

> **Note:** `show -format dot -prefix my_design_` generates the design graph in `.dot` format, which can be converted to a PDF using Graphviz.
