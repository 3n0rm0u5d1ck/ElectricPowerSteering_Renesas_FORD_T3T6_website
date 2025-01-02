---
layout: default
title: HwTq1Meas_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**HandWheel Torque 1 Measurement**

**05-Mar-2018**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Software Group,**

**Nexteer Automotive,**

**Saginaw, MI, USA  
<u>Change History</u>**

|                                                               |             |             |             |
|-------------------------------------|----------------|---------|-----------|
| **Description**                                               | **Author**  | **Version** | **Date**    |
| Initial Version                                               | Rijvi Ahmed | 1.0         | 11-Aug-2015 |
| Inplement Rack Limiter EOT                                    | Rijvi Ahmed | 2.0         | 18-Sep-2015 |
| Updated for CM660A_HwTq1Meas_Design_1.4.0                     | Selva       | 3.0         | 14-Oct-2015 |
| Updated for CM660A_HwTq1Meas_Design_1.6.0                     | Selva       | 4.0         | 21-Dec-2015 |
| Added new local function, updated Graphic, updated constants. | SPP         | 5.0         | 05-Mar-2018 |

**  
**

<u>Table of Contents</u>

[1 Introduction [5](#introduction)](#introduction)

[1.1 Purpose [5](#purpose)](#purpose)

[2 HwTq1Meas & High-Level Description
[6](#hwtq1meas-high-level-description)](#hwtq1meas-high-level-description)

[3 Design details of software module
[7](#design-details-of-software-module)](#design-details-of-software-module)

[3.1 Graphical representation of HwTq1Meas
[7](#graphical-representation-of-hwtq1meas)](#graphical-representation-of-hwtq1meas)

[3.2 Data Flow Diagram [7](#data-flow-diagram)](#data-flow-diagram)

[3.2.1 Component level DFD
[7](#component-level-dfd)](#component-level-dfd)

[3.2.2 Function level DFD [7](#function-level-dfd)](#function-level-dfd)

[4 Constant Data Dictionary
[8](#constant-data-dictionary)](#constant-data-dictionary)

[4.1 Program (fixed) Constants
[8](#program-fixed-constants)](#program-fixed-constants)

[4.1.1 Embedded Constants [8](#embedded-constants)](#embedded-constants)

[5 Software Component Implementation
[9](#software-component-implementation)](#software-component-implementation)

[5.1 Sub-Module Functions
[9](#sub-module-functions)](#sub-module-functions)

[5.1.1 Init: HwTq1MeasInit1
[9](#init-hwtq1measinit1)](#init-hwtq1measinit1)

[5.1.1.1 Design Rationale [9](#design-rationale)](#design-rationale)

[5.1.1.2 Module Outputs [9](#module-outputs)](#module-outputs)

[5.1.2 Per: HwTq1MeasPer1 [9](#per-hwtq1measper1)](#per-hwtq1measper1)

[5.1.2.1 Design Rationale [9](#design-rationale-1)](#design-rationale-1)

[5.1.2.2 Store Module Inputs to Local copies
[9](#store-module-inputs-to-local-copies)](#store-module-inputs-to-local-copies)

[5.1.2.3 (Processing of function)………
[9](#processing-of-function)](#processing-of-function)

[5.1.2.4 Store Local copy of outputs into Module Outputs
[9](#store-local-copy-of-outputs-into-module-outputs)](#store-local-copy-of-outputs-into-module-outputs)

[5.1.3 Per: HwTq1MeasPer2 [9](#per-hwtq1measper2)](#per-hwtq1measper2)

[5.1.3.1 Design Rationale [9](#design-rationale-2)](#design-rationale-2)

[5.1.3.2 Store Module Inputs to Local copies
[10](#store-module-inputs-to-local-copies-1)](#store-module-inputs-to-local-copies-1)

[5.1.3.3 (Processing of function)………
[10](#processing-of-function-1)](#processing-of-function-1)

[5.1.3.4 Store Local copy of outputs into Module Outputs
[10](#store-local-copy-of-outputs-into-module-outputs-1)](#store-local-copy-of-outputs-into-module-outputs-1)

[5.2 Server Runables [10](#server-runnables)](#server-runnables)

[5.2.1 HwTq1MeasHwTq1AutTrim_oper
[10](#hwtq1meashwtq1auttrim_oper)](#hwtq1meashwtq1auttrim_oper)

[5.2.1.1 Design Rationale
[10](#design-rationale-3)](#design-rationale-3)

[5.2.1.2 (Processing of function)………
[10](#processing-of-function-2)](#processing-of-function-2)

[5.2.2 HwTq1MeasHwTq1ClrTrim_Oper
[10](#hwtq1meashwtq1clrtrim_oper)](#hwtq1meashwtq1clrtrim_oper)

[5.2.2.1 Design Rationale
[10](#design-rationale-4)](#design-rationale-4)

[5.2.2.2 (Processing of function)………
[10](#processing-of-function-3)](#processing-of-function-3)

[5.2.3 HwTq1MeasHwTq1ReadTrim_Oper
[10](#hwtq1meashwtq1readtrim_oper)](#hwtq1meashwtq1readtrim_oper)

[5.2.3.1 Design Rationale
[10](#design-rationale-5)](#design-rationale-5)

[5.2.3.2 (Processing of function)………
[10](#processing-of-function-4)](#processing-of-function-4)

[5.2.4 HwTq1MeasHwTq1TrimPrfmdSts_Oper
[10](#hwtq1meashwtq1trimprfmdsts_oper)](#hwtq1meashwtq1trimprfmdsts_oper)

[5.2.4.1 Design Rationale
[10](#design-rationale-6)](#design-rationale-6)

[5.2.4.2 (Processing of function)………
[11](#processing-of-function-5)](#processing-of-function-5)

[5.2.5 HwTq1MeasHwTq1WrTrim_Oper
[11](#hwtq1meashwtq1wrtrim_oper)](#hwtq1meashwtq1wrtrim_oper)

[5.2.5.1 Design Rationale
[11](#design-rationale-7)](#design-rationale-7)

[5.2.5.2 (Processing of function)………
[11](#processing-of-function-6)](#processing-of-function-6)

[5.2.6 HwTq1MeasTrigStrt_Oper
[11](#hwtq1meastrigstrt_oper)](#hwtq1meastrigstrt_oper)

[5.2.6.1 Design Rationale
[11](#design-rationale-8)](#design-rationale-8)

[5.2.6.2 (Processing of function)………
[11](#processing-of-function-7)](#processing-of-function-7)

[5.3 Interrupt Functions
[11](#interrupt-functions)](#interrupt-functions)

[5.4 Module Internal (Local) Functions
[11](#module-internal-local-functions)](#module-internal-local-functions)

[5.4.1 Local Function \#1 [11](#local-function-1)](#local-function-1)

[5.4.1.1 Design Rationale
[11](#design-rationale-9)](#design-rationale-9)

[5.4.2 Local Function \#2 [11](#local-function-2)](#local-function-2)

[5.4.2.1 Design Rationale
[12](#design-rationale-10)](#design-rationale-10)

[5.5 GLOBAL Function/Macro Definitions
[12](#global-functionmacro-definitions)](#global-functionmacro-definitions)

[6 Known Limitations with Design
[13](#known-limitations-with-design)](#known-limitations-with-design)

[7 UNIT TEST CONSIDERATION
[14](#unit-test-consideration)](#unit-test-consideration)

[Appendix A Abbreviations and Acronyms
[15](#abbreviations-and-acronyms)](#abbreviations-and-acronyms)

[Appendix B Glossary [16](#glossary)](#glossary)

[Appendix C References [18](#references)](#references)

# Introduction

## Purpose

Module design document for Hand Wheel Torque 1 Measurement Function.

#  HwTq1Meas & High-Level Description

This module configures and processes the RSENT1 peripheral, which is
connected to the handwheel torque 1 sensor. The module configures the
peripheral, triggers transfers, and processes the received data.

This module also reads and provides the rack limiter EOT information
which is stored in torque sensor 1 scratchpad.

# Design details of software module

## Graphical representation of HwTq1Meas

<img
src="ElectricPowerSteering_Renesas_FORD_T3T6_website/docs/CM660A_HwTq1Meas_Impl/doc/mediax/media/image1.png"
style="width:5.73999in;height:4.22238in" />

## Data Flow Diagram

### Component level DFD

N/A

### Function level DFD

N/A

# Constant Data Dictionary

## Program (fixed) Constants

### Embedded Constants

#### Local Constants

| Constant Name        | Resolution | Units | Value |
|----------------------|------------|-------|-------|
|                      |            |       |       |
|                      |            |       |       |
| SENTSYNCTRIG_CNT_U32 | 1          | Cnt   | 16UL  |
| REGCFGWAITTI_CNT_U32 | 1          | Cnt   | 2UL   |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |
|                      |            |       |       |

Refer to .m file for other Constants.

# Software Component Implementation

## Sub-Module Functions

The sub-module functions are grouped based on similar functionality that
needs to be executed in a given “State” of the system (refer States and
Modes). For a given module, the MDD will identify the type and number of
sub-modules required. The sub-module types are described below.

## Init: HwTq1MeasInit1

## Design Rationale

Magic numbers are used due to the large number of numeric values (for
peripheral register configuration), it is more readable and easier to
maintain without using embedded constants for these values. The values
are shown in code comments, and line up exactly with the definitions
given in the design module (a special spreadsheet was included in the
design for this purpose).

See CM660A_HwTq1Meas_RSENTPeripheralCfg.xlsx in design module.

## Module Outputs

*Refer to FDD*

###  [section]

## Per: HwTq1MeasPer1

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Per: HwTq1MeasPer2

## Design Rationale

*None*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

## Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Server Runnables 

## HwTq1MeasHwTq1AutTrim_oper

## Design Rationale

*None*

##  (Processing of function)………

*See block “*HwTq1MeasHwTq1AutTrim*” in the Simulink model of the
design.*

## HwTq1MeasHwTq1ClrTrim_Oper

## Design Rationale

*None*

##  (Processing of function)…

*See block “*HwTq1MeasHwTq1ClrTrim*” in the Simulink model of the
design.*

## HwTq1MeasHwTq1ReadTrim_Oper

## Design Rationale

*None*

##  (Processing of function)…

*See block “HwTq1MeasHwTq1ReadTrim” in the Simulink model of the
design.*

## HwTq1MeasHwTq1TrimPrfmdSts_Oper

## Design Rationale

*None*

##  (Processing of function)…

*See block “HwTq1MeasHwTq1TrimPrfmdSts” in the Simulink model of the
design.*

## HwTq1MeasHwTq1WrTrim_Oper

## Design Rationale

*None*

##  (Processing of function)…

*See block “HwTq1MeasHwTq1WrTrim” in the Simulink model of the design.*

### HwTq1MeasTrigStrt_Oper

## Design Rationale

*None*

##  (Processing of function)…

*See block “HwTq1MeasTrigStrt” in the Simulink model of the design.*

## Interrupt Functions

*None*

## Module Internal (Local) Functions

## Local Function \#1

|                      |                    |      |     |     |
|----------------------|--------------------|------|-----|-----|
| **Function Name**    | RackLimrEotSigRead | Type | Min | Max |
| **Arguments Passed** | None               | N/A  | N/A | N/A |
| **Return Value**     | N/A                | N/A  | N/A | N/A |

## Design Rationale

See RackLimrEot/RackLimrEotSigRead block in the Simulink model of the
design.

## Local Function \#2

|                      |                             |      |     |     |
|----------------------|-----------------------------|------|-----|-----|
| **Function Name**    | ReadRegister                | Type | Min | Max |
| **Arguments Passed** | RegisterDummyRead_Cnt_T_u32 | N/A  | N/A | N/A |
| **Return Value**     | RegisterDummyRead_Cnt_T_u32 | N/A  | N/A | N/A |

## Design Rationale

This function can be used both for read-and-use and for read-and-discard

## Local Function \#3

|                      |              |      |     |     |
|----------------------|--------------|------|-----|-----|
| **Function Name**    | UpdRollgCntr | Type | Min | Max |
| **Arguments Passed** | None         | N/A  | N/A | N/A |
| **Return Value**     | None         | N/A  | N/A | N/A |

## Design Rationale

This function used to update the rolling counter. It uses PIM’s instead
of passing arguments. Added to reduce cyclomatic complexity.

## GLOBAL Function/Macro Definitions

None

# Known Limitations with Design

None

# UNIT TEST CONSIDERATION

Overflow for the variables **Rte_Pim_HwTq1MeasPrevRollgCntr,
Rte_Pim_HwTq1MsgMissRxCnt, Rte_Pim_HwTq1ComStsErrCntr,
Rte_Pim_HwTq1IntSnsrErrCntr** are intentional as these are used as
rolling counters.

####### Abbreviations and Acronyms

| **Abbreviation or Acronym** | **Description**           |
|-----------------------------|---------------------------|
| DFD                         | Design functional diagram |
| MDD                         | Module design Document    |

####### Glossary

**Note**: Terms and definitions from the source “Nexteer Automotive”
take precedence over all other definitions of the same term. Terms and
definitions from the source “Nexteer Automotive” are formulated from
multiple sources, including the following:

-   ISO 9000

-   ISO/IEC 12207

-   ISO/IEC 15504

-   Automotive SPICE® Process Reference Model (PRM)

-   Automotive SPICE® Process Assessment Model (PAM)

-   ISO/IEC 15288

-   ISO 26262

-   IEEE Standards

-   SWEBOK

-   PMBOK

-   Existing Nexteer Automotive documentation

| **Term** | **Definition**         | **Source** |
|----------|------------------------|------------|
| MDD      | Module Design Document |            |
| DFD      | Data Flow Diagram      |            |

####### References

| **Ref. \#** | **Title**                                                                                                                                                             | **Version**                    |
|-------|--------------------------------------------------|----------------|
| 1           | AUTOSAR Specification of Memory Mapping AUTOSAR_SWS_MemoryMapping.pdf                                                                                                 | v1.3.0 R4.0 Rev 2              |
| 2           | MDD Guideline                                                                                                                                                         | EA4 01.00.00                   |
| 3           | [Software Naming Conventions.doc](http://misagweb01.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_fc55f/Software%20Naming%20Conventions%2003x(In%20Work).doc)   | 1.02                           |
| 4           | [Software Design and Coding Standards.doc](http://eroom1.nexteer.com/eRoomReq/Files/erooms8/NextGeneration/0_1a67a9/Software%20Design%20and%20Coding%20Standards.doc) | 2.01                           |
| 5           | FDD – CM660A HwTq1Meas                                                                                                                                                | See Synergy subproject version |

{% endraw %}