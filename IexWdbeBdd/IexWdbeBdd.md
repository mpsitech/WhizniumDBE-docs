Basic device description ``[IexWdbeBdd]``
===

Schema
---

![](./IexWdbeBdd.jpg)

<p align="center"><em>Figure 1: Basic device description schema - table columns in light blue are part of the input file, table columns in dark blue are inferred</em></p>

Structure
---

[//]: # (IP structure - BEGIN)

<br>&nbsp;&nbsp;&nbsp;&nbsp;\+ System [``[ImeIMSystem]``](#1-system-imeimsystem)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\- Target [``[ImeIMTarget]``](#11-target-imeimtarget)
<br>&nbsp;&nbsp;&nbsp;&nbsp;\+ Unit [``[ImeIMUnit]``](#2-unit-imeimunit)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\- Parameters [``[ImeIAMUnitPar]``](#21-parameters-imeiamunitpar)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\+ Module [``[ImeIMModule]``](#22-module-imeimmodule)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\- Parameters [``[ImeIAMModulePar]``](#221-parameters-imeiammodulepar)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\- Controller [``[ImeIMController]``](#222-controller-imeimcontroller)
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\- Inter-module buffer [``[ImeIMImbuf]``](#223-intermodule-buffer-imeimimbuf)

[//]: # (IP structure - END)

Details
---

### 1 System

[//]: # (IP ImeIMSystem.superUse - BEGIN)

Use:

[//]: # (IP ImeIMSystem.superUse - END)

[//]: # (IP ImeIMSystem.columns - BEGIN)

Column|Content|
-|-|
srefRefWdbeMUnit (string)|root unit|
sref (string)|identifier|
Comment (string)|comment|

[//]: # (IP ImeIMSystem.columns - END)

### 1.1 Target

[//]: # (IP ImeIMTarget.superUse - BEGIN)

Super import: system (1:N)

Use:

[//]: # (IP ImeIMTarget.superUse - END)

[//]: # (IP ImeIMTarget.columns - BEGIN)

Column|Content|
-|-|
srefRefWdbeMUnit (string)|unit|
sref (string)|identifier|
rteSrefsWdbeMModule (string)|module|
Comment (string)|comment|

[//]: # (IP ImeIMTarget.columns - END)

### 2 Unit

[//]: # (IP ImeIMUnit.superUse - BEGIN)

Use:

[//]: # (IP ImeIMUnit.superUse - END)

[//]: # (IP ImeIMUnit.columns - BEGIN)

Column|Content|
-|-|
srefIxVBasetype (string)|type<br>fpga: FPGA-based<br>mcu: microcontroller-based<br>oth: other|
sref (string)|identifier|
Title (string)|name|
Comment (string)|comment|

[//]: # (IP ImeIMUnit.columns - END)

### 2.1 Parameters

[//]: # (IP ImeIAMUnitPar.superUse - BEGIN)

Super import: unit (1:N)

Use:

[//]: # (IP ImeIAMUnitPar.superUse - END)

[//]: # (IP ImeIAMUnitPar.columns - BEGIN)

Column|Content|
-|-|
x1SrefKKey (string)|key<br>mnf: manufacturer<br>partno: part number<br>toolch: tool chain|
osrefKVal (string)|value<br>mchp: Microchip<br>xlnx: Xilinx<br>pic24f16kl402/ss: PIC24 16MHz SSOP28<br>xc3s100e-vqg100: Spartan-3E 100 QFP100<br>xc3s100e-cpg132: Spartan-3E 100 BGA132<br>xc3s250e-4vqg100: Spartan-3E 250 QFP100<br>xc3s500e-4vqg100: Spartan-3E 500 QFP100<br>xc3s500e-fgg320: Spartan-3E 500 BGA320<br>xc7a35t-1cpg236: Artix-7 35 BGA236<br>xc7a100t-2fgg484c: Artix-7 100 BGA484<br>xc7z020-clg484-1: Zynq 7020 BGA484<br>xczu3eg-sfva625-1: Zynq UltraScale+ EG BGA625<br>ise: Xilinx ISE<br>mplab: Microchip MPLAB X<br>vivado: Xilinx Vivado<br>vivzynq: Xilinx Vivado for Zynq|

[//]: # (IP ImeIAMUnitPar.columns - END)

### 2.2 Module

[//]: # (IP ImeIMModule.superUse - BEGIN)

Super import: unit (1:N)

Use:

[//]: # (IP ImeIMModule.superUse - END)

[//]: # (IP ImeIMModule.columns - BEGIN)

Column|Content|
-|-|
srefIxVBasetype (string)|type<br>top: top<br>hostif: host interface<br>ehostif: easy model host interface<br>cmdbus: command bus controller<br>cmdinv: command invocation buffer<br>cmdret: command return buffer<br>imbuf: inter-module buffer<br>mnfcore: manufacturer core<br>mnfprim: manufacturer primitive<br>ctr: controller<br>fwdctr: forwarding controller<br>ectr: easy model controller<br>wrp: wrapper<br>oth: other|
hsrefSupRefWdbeMModule (string)|super module|
srefTplRefWdbeMModule (string)|template|
sref (string)|identifier|
Comment (string)|comment|

[//]: # (IP ImeIMModule.columns - END)

### 2.2.1 Parameters

[//]: # (IP ImeIAMModulePar.superUse - BEGIN)

Super import: module (1:N)

Use:

[//]: # (IP ImeIAMModulePar.superUse - END)

[//]: # (IP ImeIAMModulePar.columns - BEGIN)

Column|Content|
-|-|
x1SrefKKey (string)|key|
Val (string)|value|

[//]: # (IP ImeIAMModulePar.columns - END)

### 2.2.2 Controller

[//]: # (IP ImeIMController.superUse - BEGIN)

Super import: module (1:1)

Use:

[//]: # (IP ImeIMController.superUse - END)

[//]: # (IP ImeIMController.columns - BEGIN)

Column|Content|
-|-|
srefFwdRefWdbeMUnit (string)|unit forwarded to|

[//]: # (IP ImeIMController.columns - END)

### 2.2.3 Inter-module buffer

[//]: # (IP ImeIMImbuf.superUse - BEGIN)

Super import: module (1:1)

Use:

[//]: # (IP ImeIMImbuf.superUse - END)

[//]: # (IP ImeIMImbuf.columns - BEGIN)

Column|Content|
-|-|
hsrefCorRefWdbeMModule (string)|corresponding module|
sref (string)|identifier|
srefIxVDir (string)|direction<br>in: input<br>out: output|

[//]: # (IP ImeIMImbuf.columns - END)

<em>Markdown for WhizniumDBE 0.9.42 auto-generated (what else ;-) ) by WhizniumSBE on 16 Sep 2018</em>
