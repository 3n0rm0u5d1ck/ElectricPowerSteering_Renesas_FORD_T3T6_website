---
layout: default
title: MotCtrlPrmEstimn_MDD
nav_order: 2
parent: Component Implementation
---
{% raw %}
**Module Design Document**

**For**

**MotCtrlPrmEstimn**

**VERSION: 4.0**

**DATE: 25-Sep-2017**

**Prepared By:**

**TATA,**

**Trivandrum, India**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|             |                                                                    |            |             |               |
|-----|-----------------------------------|------------|---------|------------|
| **Sl. No.** | **Description**                                                    | **Author** | **Version** | **Date**      |
| 1           | Initial Version                                                    | Rijvi      | 1.0         | 20-JUN-2015   |
| 2           | Updated per design rev. 1.5.0                                      | Rijvi      | 2.0         | 07-APRIL-2016 |
| 3           | Updated per design rev. 2.1.0                                      | ML         | 3.0         | 29-NOV-2016   |
| 4           | New Input added MotAndThermProtnLoaMod and deleted IvtrLoaMtgtnEna | TATA       | 4.0         | 25-SEP-2017   |
|             |                                                                    |            |             |               |

Table of Contents

[1 Abbrevations And Acronyms 5](#abbrevations-and-acronyms)

[2 References 6](#references)

[3 MotCtrlPrmEstimn & High-Level Description
7](#motctrlprmestimn-high-level-description)

[4 Design details of software module
8](#design-details-of-software-module)

[4.1 Graphical representation of MotCtrlPrmEstimn
8](#graphical-representation-of-motctrlprmestimn)

[4.2 Data Flow Diagram 9](#data-flow-diagram)

[4.2.1 Module level DFD 9](#module-level-dfd)

[4.2.2 Sub-Module level DFD 9](#sub-module-level-dfd)

[4.3 COMPONENT FLOW DIAGRAM 9](#component-flow-diagram)

[5 Variable Data Dictionary 10](#variable-data-dictionary)

[5.1 User defined typedef definition/declaration
10](#user-defined-typedef-definitiondeclaration)

[5.2 Variable definition for enumerated types
10](#variable-definition-for-enumerated-types)

[6 Constant Data Dictionary 11](#constant-data-dictionary)

[6.1 Program(fixed) Constants 11](#programfixed-constants)

[6.1.1 Embedded Constants 11](#embedded-constants)

[6.1.1.1 Local 11](#local)

[6.1.1.2 Global 11](#global)

[6.1.2 Module specific Lookup Tables Constants
11](#module-specific-lookup-tables-constants)

[7 Software Module Implementation 12](#software-module-implementation)

[7.1 Sub-Module Functions 12](#sub-module-functions)

[7.2 Initialization Functions 12](#initialization-functions)

[7.2.1 Per: MotCtrlPrmEstimnInit1 12](#per-motctrlprmestimninit1)

[7.2.1.1 Design Rationale 12](#design-rationale)

[7.2.1.2 Store Module Inputs to Local copies
12](#store-module-inputs-to-local-copies)

[7.2.1.3 (Processing of function)……… 12](#processing-of-function)

[7.2.1.4 Store Local copy of outputs into Module Outputs
12](#store-local-copy-of-outputs-into-module-outputs)

[7.3 PERIODIC FUNCTIONS 12](#periodic-functions)

[7.3.1 Per: MotCtrlPrmEstimnPer1 12](#per-motctrlprmestimnper1)

[7.3.1.1 Design Rationale 12](#design-rationale-1)

[7.3.1.2 Store Module Inputs to Local copies
12](#store-module-inputs-to-local-copies-1)

[7.3.1.3 (Processing of function)……… 12](#processing-of-function-1)

[7.3.1.4 Store Local copy of outputs into Module Outputs
12](#store-local-copy-of-outputs-into-module-outputs-1)

[7.3.2 Per: MotCtrlPrmEstimnPer2 12](#per-motctrlprmestimnper2)

[7.3.2.1 Design Rationale 12](#design-rationale-2)

[7.3.2.2 Store Module Inputs to Local copies
12](#store-module-inputs-to-local-copies-2)

[7.3.2.3 (Processing of function)……… 12](#processing-of-function-2)

[7.3.2.4 Store Local copy of outputs into Module Outputs
13](#store-local-copy-of-outputs-into-module-outputs-2)

[7.4 Non PERIODIC FUNCTIONS 13](#non-periodic-functions)

[7.5 Interrupt Functions 13](#__RefHeading___Toc494125641)

[7.6 Server runnables 13](#server-runnables)

[7.6.1 GetMotPrmNomEol 13](#getmotprmnomeol)

[7.6.1.1 Design Rationale 13](#design-rationale-3)

[7.6.1.2 Store Module Inputs to Local copies
13](#store-module-inputs-to-local-copies-3)

[7.6.1.3 (Processing of function)……… 13](#processing-of-function-3)

[7.6.1.4 Store Local copy of outputs into Module Outputs
13](#store-local-copy-of-outputs-into-module-outputs-3)

[7.6.2 SetMotPrmNomEol 13](#setmotprmnomeol)

[7.6.2.1 Design Rationale 13](#design-rationale-4)

[7.6.2.2 Store Module Inputs to Local copies
13](#store-module-inputs-to-local-copies-4)

[7.6.2.3 (Processing of function)……… 13](#processing-of-function-4)

[7.6.2.4 Store Local copy of outputs into Module Outputs
13](#store-local-copy-of-outputs-into-module-outputs-4)

[7.7 Serial Communication Functions 14](#serial-communication-functions)

[7.8 Local Function/Macro Definitions
14](#local-functionmacro-definitions)

[7.8.1 Local Function \#1 CalcCurrMagSqRef
14](#local-function-1-calccurrmagsqref)

[7.9 GLObAL Function/Macro Definitions
14](#global-functionmacro-definitions)

[7.10 TRANSIENT FUNCTIONS 14](#transient-functions)

[8 Unit Test Considerations 15](#unit-test-considerations)

[9 Known Limitations With Design 16](#known-limitations-with-design)

[10 Appendix 17](#appendix)

# Abbrevations And Acronyms

|              |                                         |
|--------------|-----------------------------------------|
| Abbreviation | Description                             |
| DFD          | Design functional diagram               |
| MDD          | Module design Document                  |
|              | \<ADD more to the table if applicable\> |
|              |                                         |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|         |                                      |                                |
|----------|----------------------------------------------|-----------------|
| Sr. No. | Title                                | Version                        |
| \<1\>   | \<MDD Guidelines\>                   | Process 4.02.00                |
| \<2\>   | \<Software Naming Conventions\>      | Process 4.02.00                |
| \<3\>   | \<Coding standards\>                 | 2.1                            |
| \<4\>   | FDD - SF102A_MotCtrlPrmEstimn_Design | See Synergy Subproject version |
|         | \<Add if more available\>            |                                |

# MotCtrlPrmEstimn & High-Level Description

Please refer FDD

# Design details of software module

## Graphical representation of MotCtrlPrmEstimn

<img
src="ElectricPowerSteering_Renesas_FORD_T3T6_website/docs/SF102A_MotCtrlPrmEstimn_Impl/doc/mediax/media/image2.png"
style="width:4.23958in;height:6.04167in" />

## Data Flow Diagram

## Module level DFD

## Sub-Module level DFD

## COMPONENT FLOW DIAGRAM

# Variable Data Dictionary

## User defined typedef definition/declaration 

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 31%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Typedef Name</td>
<td>Element Name</td>
<td>User Defined Type</td>
<td><p>Legal Range</p>
<p>(min)</p></td>
<td><p>Legal Range</p>
<p>(max)</p></td>
</tr>
<tr class="even">
<td>None</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Variable definition for enumerated types

|           |                                          |                       |
|--------------------------------|-----------------------------|------------|
| Enum Name | Element Name                             | Value                 |
| N/A       | \<(Variable name qualified Refer\[2\])\> | \<Define the value \> |

# Constant Data Dictionary

## Program(fixed) Constants

## Embedded Constants

*\< All program specific constants will be defined in detail \>*

## Local

|                              |            |       |       |
|------------------------------|------------|-------|-------|
| Constant Name                | Resolution | Units | Value |
| Refer constants from .m file |            |       |       |
| BITMASK2_CNT_U08             | 1          | Cnt   | 2U    |

## Global

*\<This section lists the global constants used by the module. For
details on global constants, refer to the Data Dictionary for the
application\>*

|               |
|---------------|
| Constant Name |
| None          |

## Module specific Lookup Tables Constants

*\<(This is for lookup tables (arrays) with fixed values, same name as
other tables)\>*

|               |            |       |                  |
|---------------|------------|-------|------------------|
| Constant Name | Resolution | Value | Software Segment |
| None          |            |       |                  |

# Software Module Implementation

## Sub-Module Functions

*NONE*

## Initialization Functions

## Per: MotCtrlPrmEstimnInit1

## Design Rationale

*Refer to FDD*

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

##  Store Local copy of outputs into Module Outputs

*Refer to FDD*

## PERIODIC FUNCTIONS 

## Per: MotCtrlPrmEstimnPer1

## Design Rationale

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

##  Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Per: MotCtrlPrmEstimnPer2

## Design Rationale

## Store Module Inputs to Local copies

*Refer to FDD*

## (Processing of function)………

*Refer to FDD*

##  Store Local copy of outputs into Module Outputs

*Refer to FDD*

## Non PERIODIC FUNCTIONS 

*None*

## Interrupt Functions

*None*

## Server runnables

## GetMotPrmNomEol

##  Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*See* GetMotPrmNomEol *block in the FDD*

## Store Local copy of outputs into Module Outputs

*None*

## SetMotPrmNomEol 

## Design Rationale

*None*

## Store Module Inputs to Local copies

*None*

## (Processing of function)………

*See* SetMotPrmNomEol *block in the FDD*

## Store Local copy of outputs into Module Outputs

*None*

## Serial Communication Functions

*None*

## Local Function/Macro Definitions

## Local Function \#1 CalcCurrMagSqRef

None

## GLObAL Function/Macro Definitions

None

## TRANSIENT FUNCTIONS 

None

# Unit Test Considerations

None

# Known Limitations With Design

CurrMeasLoaMtgtnEna and FetLoaMtgtnEna are terminated. These flags need
not be computed at all.

# Appendix

*None*

{% endraw %}