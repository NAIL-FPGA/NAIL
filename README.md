# NAIL
### The NAIL Accelerator Framework - an offload system for FPGA-based acceleration

NAIL is a low-latency FPGA offload framework, using PCIe to enable efficient control & communication. Full details on design can be found in our research papers.

As a summary, on the firmware side, NAIL provides a wrapper for up to four "cores", These cores can implement an arbitrary function based on packet-based command, PCIe data, board utility and results interfaces. Core software drivers then present interfaces with these cores in SysFS, with some example software to perform the necessary interactions to use NAIL.

To build NAIL firmware, we use Fusesoc: https://github.com/olofk/fusesoc. This is a highly-effective open-source build system, which includes dependency resolution and tool invocation. Sadly, the term "core" is overloaded, being used for NAIL functions but also a dependency unit in Fusesoc. To start a build, use the command `fusesoc run --target build --tool <tool> --pnr <router> <name> -- <tool args>`. These fields are:
* --tool: the synthesis tool you wish to use, such as Quartus or Vivado
* --pnr: the placement and routing tool you want, such as DSE or Vivado
* Core name: this is the top-level core name taken from the relevant field in NAIL-TEST or NAIL-SHELL.
* Tool args: any arguments that you wish to pass to the build tool.
