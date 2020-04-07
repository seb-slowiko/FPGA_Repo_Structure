# (**Enter board name here**) Mi-V Sample FPGA Designs
This folder contains Tcl scripts that build Libero SoC **(vUpdate version number)** design projects for the (**Enter board name here**). These scripts are executed in Libero SoC to generate the sample designs.

## <a name="quick"></a> Instructions

#### Selecting type of MiV core
The top level TCL files in the Libero_Projects folder correspond to the type of core that is to be used in the design. Pick the type you want and move onto the next step.

Top level script files:
| TCL filename                         |  Description                                             |
| ------------------------------------ |:--------------------------------------------------------:|
| (Board Name)-MiV_RV32IMA_BaseDesign   | Generate a sample design with the MiV_RV32IMA_L1_AHB or MiV_RV32IMA_L1_AXI core  |
| (Board Name)-MiV_RV32IMAF_BaseDesign  | Generate a sample design with the MiV_RV32IMAF_L1_AHB core                       |
| (Board Name)-MiV_RV32IMC_BaseDesign   | Generate a sample design with the MiV_RV32IMC core                               |


#### Running Libero SoC in GUI mode
    1. Open Libero SoC
    2. Execute the script, Project -> Execute Script
    3. Select the directory that the script is located in using the "..."
    4. Select the script and select "Open"
    5. In the arguments text box, enter type of configuration you want e.g. "CFG1"
    6. Select the "Run" button to execute the script
    7. Once complete, a script report will be generated.

Libero executes the script and opens the Mi-V sample project. The script adds Timing constraints to the project for Synthesis, Place and Route, and Timing Verification. Additionally, IO Constraints are added to the project for Place and Route. The project can now be taken through the remainder of the Libero SoC design flow.

#### Running Libero SoC in GUI mode, with Script Arguments
    1. Open Libero SoC
    2. Execute the selected script, Project -> Execute Script
    3. Select the directory that the script is located in, using the "..."
    4. Select the script and select "Open"
    5. In the arguments text box, enter "CFG1 SYNTHESIZE"
    6. Select the "Run" button to execute the script
    7. Once complete, a script report will be generated.

In this example, the arguments "CFG1 SYNTHESIZE" are entered to take the project through to Synthesis.

Libero executes the script and opens the Mi-V sample project. The script adds Timing constraints to the project for Synthesis, Place and Route, and Timing Verification. Additionally, IO Constraints are added to the project for Place and Route. The project can now be taken through the remainder of the Libero SoC design flow.

## <a name="Script arguments"></a> Script Arguments
In the examples above the arguments "CFG1" and "CFG1 SYNTHESIZE" were entered. The complete set of script arguments are documented here.

First argument:
| Argument    |  Description   |
| ------------- |:-------------:|
| CFG1      | Generate a sample design with the AHB interface support  |
| CFG2      | Generate a sample design with the AXI3 interface support |
| CFG3      | Generate a sample design with the AXI4 interface support |
| CFG4      | Generate a sample design with the TCM interface support  |

Second argument:
| Argument    |  Description   |
| ------------- |:-------------:|
| SYNTHESIZE | Run synthesis on the design  |
| PLACE_AND_ROUTE | Run place and route on the design  |
| GENERATE_BITSTREAM | Generate the bitstream for the design|
| EXPORT_PROGRAMMING_FILE | Export the programming file (.job) |

## Design Features
The Libero designs include the following features:
* A choice of the soft RISC-V processor:
  - MIV_RV32IMA_L1_AHB
  - MIV_RV32IMA_L1_AXI
  - MiV_RV32IMAF_L1_AHB
  - MiV_RV32IMC
* RISC-V debug block allowing on-target debug using SoftConsole.
* The operating frequency of the design is 50MHz.
* Target memory is LSRAM.
* User peripherals (GPIO, Timers, UART).

The peripherals in this design are located at the following addresses.

| Peripheral    | Address   |
| ------------- |:-------------:|
| CoreUARTapb   | 0x7000_1000   |
| CoreGPIO_IN   | 0x7000_2000   |
| CoreTimer_0   | 0x7000_3000   |
| CoreTimer_1   | 0x7000_4000   |
| CoreGPIO_OUT  | 0x7000_5000   |
| LSRAM| 0x8000_0000|
