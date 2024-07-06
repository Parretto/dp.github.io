---
layout: page
title: Build
permalink: /build/
nav_order: 7
---

# Build

### Repository
The DP IP-cores and reference design can be downloaded from the [Github repository](https://github.com/Parretto/DisplayPort)

The repository file structure is listed below;


```
  .
  ├── gateware
  │   ├── src                       - Source folder
  │   │   ├── lib                     - Library
  │   │   ├── app                     - Application
  │   │   ├── risc-v                  - RISC-V
  │   │   ├── misc                    - Miscellaneous
  │   |   ├── pm                      - Policy maker
  │   │   ├── rx                      - DP RX
  │   │   ├── tx                      - DP TX
  │   │   ├── vtb                     - Video toolbox
  │   │   └── scaler                  - Scaler
  │   ├── ref                       - Reference folder
  │   │   ├── amd                     - AMD
  │   │   |   ├── zcu102                - ZCU102 evbaluation kit
  │   │   │   └── tb-a7-200t-img        - Inrevium TB-A7-200T-IMG evaluation kit
  │   │   ├── intel                   - Intel
  │   │   |   ├── dk-dev-10cx220        - Cyclone 10 GX development board   
  │   │   │   └── dk-dev-10ax115s       - Arria 10 GX development board
  │   │   └── lsc                     - Lattice
  │   │       └── lfcpnx_evn            - CertusPro-NX evaluation board
  │   └── syn                       - Synthesis folder
  │       ├── amd                     - AMD
  │       ├── intel                   - Intel
  │       └── lsc                     - Lattice
  └── software
      ├── src                       - Source folder
      │   ├── app                     - Application
      │   ├── lib                     - Library
      │   └── vtb                     - Video toolbox
      └── build                     - Build folder
          └── bin                     - Binaries

```

<br>

-----

### Reference design
Below are the steps to build the reference design for both gateware and software. 

Before building the reference design application you have to install the RISC-V GNU Compiler Toolchain. 
For more information click [here](https://github.com/riscv-collab/riscv-gnu-toolchain)

In the cmake commandline the argument GCC points to the Risc-V toolchain; eg. -DGCC=/riscv32/bin/riscv32-unknown-elf-



<br>
**AMD ZCU102 reference design**
1. Change the directory to the folder gateware/syn/amd
2. Run the TCL build script; vivado -mode batch -source ../../ref/amd/zcu102/build_proj.tcl
3. Change the directory to the folder software/build
4. Run the cmake command; cmake . -DVENDOR=AMD -DBOARD=AMD_ZCU102 -DGCC=\<gcc toolchain\>
5. Then run make to build the binaries

<br>
**AMD TB-A7-200T-IMG reference design**
1. Change the directory to the folder gateware/syn/amd
2. Run the TCL build script; vivado -mode batch -source ../../ref/amd/tb-a7-200t-img/build_proj.tcl
3. Change the directory to the folder software/build
4. Run the cmake command; cmake . -DVENDOR=AMD -DBOARD=TB_A7_200T_IMG -DGCC=\<gcc toolchain\>
5. Then run make to build the binaries

<br>
**Intel Cyclone 10GX reference design**
1. Change the directory to the folder gateware/syn/intel
2. Run the TCL build script; quartus_sh -t ../../ref/intel/dk-dev-10cx220/build_proj.tcl
3. Change the directory to the folder software/build
4. Run the cmake command; cmake . -DVENDOR=INT -DBOARD=INT_C10GX -DGCC=\<gcc toolchain\>
5. Then run make to build the binaries

<br>
**Intel Arria 10GX reference design**
1. Change the directory to the folder gateware/syn/intel
2. Run the TCL build script; quartus_sh -t ../../ref/intel/dk-dev-10ax115s/build_proj.tcl
3. Change the directory to the folder software/build
4. Run the cmake command; cmake . -DVENDOR=INT -DBOARD=INT_A10GX -DGCC=\<gcc toolchain\>
5. Then run make to build the binaries

<br>
**Lattice reference design**
1. Change the directory to the folder gateware/syn/lsc
2. Run the TCL build script; radiantc -source ../../ref/lsc/lfcpnx_evn/build_proj.tcl
3. Change the directory to the folder software/build
4. Run the cmake command; cmake . -DVENDOR=LSC -DBOARD=LSC_LFCPNX -DGCC=\<gcc toolchain\>
5. Then run make to build the binaries

-----
