---
layout: default
title: SysFricLrng_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**SysFricLrng**

**VERSION: 5.0**

**DATE:** **04-Oct-2017**

**Prepared By:**

**Matthew Leser**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Location:** The official version of this document is stored in the
Nexteer Configuration Management System.

**Revision History**

|            |                                      |                       |             |             |
|-----|--------------------|--------------------|---------|--------------------|
| **Sl. No** | **Description**                      | **Author**            | **Version** | **Date**    |
| 1          | Initial version                      | Basavaraja Ganeshappa | 1.0         | 30-Mar-2016 |
| 2          | Updated to design version 2.2.0      | TATA                  | 2.0         | 05-Dec-16   |
| 3          | Updated to design version 2.4.0      | KK                    | 3.0         | 28-Feb-17   |
| 4          | Remove notes for Integrator Settings | KK                    | 4.0         | 28-Mar-17   |
| 5          | Added new Non Rte Server Runnable    | ML                    | 5.0         | 04-Oct-17   |

Table of Contents

[1 Abbrevations And Acronyms 4](#abbrevations-and-acronyms)

[2 References 5](#references)

[3 Dependencies 6](#dependencies)

[3.1 SWCs 6](#swcs)

[3.2 Global Functions(Non RTE) to be provided to Integration Project
6](#global-functionsnon-rte-to-be-provided-to-integration-project)

[4 Configuration REQUIREMeNTS 7](#configuration-requirements)

[4.1 Build Time Config 7](#build-time-config)

[4.2 Configuration Files to be provided by Integration Project
7](#configuration-files-to-be-provided-by-integration-project)

[4.3 Da Vinci Parameter Configuration Changes
7](#da-vinci-parameter-configuration-changes)

[4.4 DaVinci Interrupt Configuration Changes
7](#__RefHeading___Toc468713243)

[4.5 Manual Configuration Changes 7](#manual-configuration-changes)

[5 Integration DATAFLOW REQUIREMENTS
8](#integration-dataflow-requirements)

[5.1 Required Global Data Inputs 8](#required-global-data-inputs)

[5.2 Required Global Data Outputs 8](#required-global-data-outputs)

[5.3 Specific Include Path present 8](#specific-include-path-present)

[6 Runnable Scheduling 9](#runnable-scheduling)

[7 Memory Map REQUIREMENTS 10](#memory-map-requirements)

[7.1 Mapping 10](#mapping)

[7.2 Usage 10](#usage)

[7.3 NvM Blocks 10](#nvm-blocks)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

[9 Appendix 12](#appendix)

# Abbrevations And Acronyms

|                  |                            |
|------------------|----------------------------|
| **Abbreviation** | **Description**            |
| DFD              | Design functional diagram  |
| FDD              | Functional Design Document |
| MDD              | Module design Document     |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                      |                                 |
|----------|-------------------------------------------|--------------------|
| **Sr. No.** | **Title**                            | **Version**                     |
| 1           | MDD Guideline                        | Process 4.02.01                 |
| 2           | EA4 Software Naming Conventions      | Process 4.02.01                 |
| 3           | Software Design and Coding Standards | Process 4.02.01                 |
| 4           | FDD: SF007A_SysFricLrng_Design       | See Synergy sub project version |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   |                      |

## Global Functions(Non RTE) to be provided to Integration Project

> FricLrngShtDwn

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

> None

## Da Vinci Parameter Configuration Changes

|               |           |         |
|---------------|-----------|---------|
| **Parameter** | **Notes** | **SWC** |
| **None**      |           |         |

## DaVinci Interrupt Configuration Changes

|              |            |                         |           |
|--------------|------------|-------------------------|-----------|
| **ISR Name** | **VIM \#** | **Priority Dependency** | **Notes** |
| **None**     |            |                         |           |

## Manual Configuration Changes

|              |           |         |
|--------------|-----------|---------|
| **Constant** | **Notes** | **SWC** |
| **None**     |           |         |

# Integration DATAFLOW REQUIREMENTS

## Required Global Data Inputs

> Refer SF007A_SysFricLrng_DataDict.m

## Required Global Data Outputs

> Refer SF007A_SysFricLrng_DataDict.m

## Specific Include Path present

> Yes

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                     |                             |             |
|---------------------|-----------------------------|-------------|
| **Init**            | **Scheduling Requirements** | **Trigger** |
| **StOutpCtrlInit1** | None                        | RTE – Init  |

|                    |                             |             |
|--------------------|-----------------------------|-------------|
| **Runnable**       | **Scheduling Requirements** | **Trigger** |
| **StOutpCtrlPer1** | None                        | RTE – 10ms  |

<table style="width:100%;">
<colgroup>
<col style="width: 25%" />
<col style="width: 54%" />
<col style="width: 20%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Server Runnable</strong></td>
<td><strong>Scheduling Requirements</strong></td>
<td><strong>Trigger</strong></td>
</tr>
<tr class="even">
<td><strong>ClrFricLrngOperMod</strong></td>
<td>None</td>
<td>On server invocation call</td>
</tr>
<tr class="odd">
<td><strong>GetFricLrngData</strong></td>
<td>None</td>
<td>On server invocation call</td>
</tr>
<tr class="even">
<td><strong>GetFricOffsOutpDi</strong></td>
<td>None</td>
<td>On server invocation call</td>
</tr>
<tr class="odd">
<td><strong>InitFricLrngTbl</strong></td>
<td>None</td>
<td>On server invocation call</td>
</tr>
<tr class="even">
<td><strong>SetFricLrngData</strong></td>
<td>None</td>
<td>On server invocation call</td>
</tr>
<tr class="odd">
<td><strong>SetFricOffsOutpDi</strong></td>
<td>None</td>
<td>On server invocation call</td>
</tr>
<tr class="even">
<td><strong>GetFricData</strong></td>
<td>None</td>
<td>On server invocation call</td>
</tr>
<tr class="odd">
<td><strong>SetFricData</strong></td>
<td>None</td>
<td>On server invocation call</td>
</tr>
<tr class="even">
<td><strong>FricLrngShtDwn</strong></td>
<td><p>Non Rte Server Runnable. This should be called before</p>
<p>the Nvm WriteAll and Shutdown.</p></td>
<td>On server invocation call</td>
</tr>
</tbody>
</table>

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
|                    |              |           |
|                    |              |           |

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

-   Refer Data Dict

# Compiler Settings

##  Preprocessor MACRO

> ***FLTINJENA** is used for coditionaly injecting fault*

## Optimization Settings

None

# Appendix

*None*

{% endraw %}