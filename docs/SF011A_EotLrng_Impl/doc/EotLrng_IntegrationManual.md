---
layout: default
title: EotLrng_IntegrationManual
nav_order: 1
parent: Component Implementation
---
{% raw %}
**Integration Manual**

**For**

**End of Travel Learning (SF011A)**

**VERSION:** **4.0**

**DATE:** **14-March-2017**

**Prepared For:**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Prepared By:**

**Matthew Leser,**

**Software Engineering**

**Nexteer Automotive,**

**Saginaw, MI, USA**

**Revision History**

|             |                                 |                   |             |             |
|---------|-----------------|-------------------|--------|--------------------|
| **Sl. No.** | **Description**                 | **Author**        | **Version** | **Date**    |
| 1           | Initial version                 | Akhil Krishna N D | 1.0         | 09/24/2015  |
| 2           | Updated for v2.0.0 of FDD       | Nick Saxton       | 2.0         | 05/19/2016  |
| 3           | Updated to design version 3.1.0 | TATA              | 3.0         | 05-Dec-16   |
| 4           | Updated to design version 3.2.0 | ML                | 4.0         | 14-March-17 |

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
7](#__RefHeading___Toc430697828)

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

[1.1 RTE NvM Blocks 10](#rte-nvm-blocks)

[8 Compiler Settings 11](#compiler-settings)

[8.1 Preprocessor MACRO 11](#preprocessor-macro)

[8.2 Optimization Settings 11](#optimization-settings)

[9 Appendix 12](#appendix)

# Abbrevations And Acronyms

|                  |                           |
|------------------|---------------------------|
| **Abbreviation** | **Description**           |
| DFD              | Design functional diagram |
| MDD              | Module design Document    |
|                  |                           |

# References

This section lists the title & version of all the documents that are
referred for development of this document

|             |                                      |                                 |
|----------|----------------------------------------------|-----------------|
| **Sr. No.** | **Title**                            | **Version**                     |
| 1           | FDD : SF011A_EotLrng_Design          | See Synergy sub project version |
| 2           | Software Naming Conventions          | Process 4.02.00                 |
| 3           | Software Design and Coding Standards | 2.1                             |

# Dependencies

## SWCs

|            |                      |
|------------|----------------------|
| **Module** | **Required Feature** |
| **None**   | N/A                  |

Note : Referencing the external components should be avoided in most
cases. Only in unavoidable circumstance external components should be
referred. Developer should track the references.

## Global Functions(Non RTE) to be provided to Integration Project

None

# Configuration REQUIREMeNTS

## Build Time Config

|             |           |     |
|-------------|-----------|-----|
| **Modules** | **Notes** |     |
| **None**    |           |     |

## Configuration Files to be provided by Integration Project

None

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

Refer DataDict.m file.

## Required Global Data Outputs

Refer DataDict.m file.

## Specific Include Path present

No

# Runnable Scheduling 

This section specifies the required runnable scheduling.

|                  |                             |             |
|------------------|-----------------------------|-------------|
| **Init**         | **Scheduling Requirements** | **Trigger** |
| **EotLrngInit1** | None                        | RTE(Init)   |

|                        |                             |             |
|------------------------|-----------------------------|-------------|
| **Runnable**           | **Scheduling Requirements** | **Trigger** |
| **EotLrngPer1**        | None                        | RTE (10 ms) |
| **SerlComRstEot_Oper** | None                        | On event    |
| **RtnMaxHwAgCwAndCcw** | None                        | On event    |
| **RstMaxHwAgCwAndCcw** | None                        | On event    |
| **GetHwAgOverTrvlCnt** | None                        | On event    |
| **RstHwAgOverTrvlCnt** | None                        | On event    |
| **SetHwAgOverTrvlCnt** | None                        | On event    |

# Memory Map REQUIREMENTS

## Mapping

|                    |              |           |
|--------------------|--------------|-----------|
| **Memory Section** | **Contents** | **Notes** |
| **None**           |              |           |
|                    |              |           |

\* Each …START_SEC… constant is terminated by a …STOP_SEC… constant as
specified in the AUTOSAR Memory Mapping requirements.

## Usage

|             |         |         |
|-------------|---------|---------|
| **Feature** | **RAM** | **ROM** |
| **None**    |         |         |

Table 1: ARM Cortex R4 Memory Usage

## NvM Blocks

NOTE: In Autosar, Store at Shutdown and Restore at Startup were turned
off for NVM Block Needs for NvmMaxHwAgCwAndCcw and NvmEotNvmData. This
was done to remove warnings given during check. These will need to be
turned back on during integration.

## RTE NvM Blocks

|                     |
|---------------------|
| **Block Name**      |
| **EotNvmData**      |
| **MaxHwAgCwAndCcw** |

# Compiler Settings

## Preprocessor MACRO

None.

## Optimization Settings

None.

# Appendix

None

{% endraw %}