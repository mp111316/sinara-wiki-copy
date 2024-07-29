Software control infrastructure known to be in use on ion trap experiments:

|Name              | Origin                     | Link                             | Comment |
|-----             |----                        |-----                             | ------  |
|ARTIQ             | M-Labs, NIST Boulder, 2013-present | [github](https://github.com/m-labs/artiq)| | 
|HFGui             | NIST Ion Storage, 2002-2017 |         | No active development. Migrating to ARTIQ/Sinara.       |
|Aluminizer        | NIST Ion Storage, 2006-present     | [github](https://github.com/nist-ionstorage/ionizer)| Written by Till Rosenband.  Used in the ion clock lab at NIST and maintained there by David Leibrandt.|
| Ion Control      | Duke, Sandia, 2008-present               | [github](https://github.com/pyIonControl) | Written and maintained by Peter Maunz at Sandia.  Also used by Monroe lab at UMD and Kim lab at Duke. Limited active development by Sandia. |
|M-ACTION          | ETH Zurich                 | [Vlad's Thesis](https://www.research-collection.ethz.ch/bitstream/handle/20.500.11850/295923/Thesis_VNegnevitsky.pdf)  [Mentioned in this paper](https://arxiv.org/abs/1705.02771) | |
|LabRad   | UCSB ??-present                 | [github](https://github.com/labrad/) [AMOLabRAD](https://github.com/AMOLabRAD/AMOLabRAD/wiki/)  [LabRAD Tools](https://github.com/HaeffnerLab/Haeffner-Lab-LabRAD-Tools/)| Originally developed by the Martinis Lab at UCSB for superconducting experiments.  AMOLabRAD and LabRAD tools are part of an effort by Haeffner Lab at Berkeley to use LabRAD in ion trap setups. Limited active development. | 
|TRiCS (Trapped Ion Control System) | Innsbruck | Mentioned briefly in [thesis1](https://quantumoptics.at/images/publications/dissertation/2017_guggemos_diss.pdf), [thesis2](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwjYmIennp_bAhWwt1kKHf4hCKMQFggpMAA&url=https%3A%2F%2Fquantumoptics.at%2Fimages%2Fpublications%2Fdiploma%2Fdiplom_pauli.pdf&usg=AOvVaw3WNj7LnfLWwBLVv177FxWq) and [thesis3](http://www.diva-portal.org/smash/get/diva2:1203307/FULLTEXT01.pdf) | Developed by in-house programmer in Blatt lab at Innsbruck.  Also used by the Hennrich lab in Stockholm. No public source. Little active development.|
|MasterControlProgram [MCP] | University Kassel | | Developed be Kilian Singer. No public source known.|
|Pulse Sequencer | MIT 2002-2010 | [WBM](https://web.archive.org/web/20140105044601/http://pulse-programmer.org/) [WP](https://en.wikipedia.org/wiki/Pulse_programming) | Designed by Paul Pham. No active development |
| The Cicero Word Generator| MIT Ketterle lab -2012 | [arXiv](https://arxiv.org/abs/1208.2607) [github](https://github.com/akeshet/Cicero-Word-Generator) | designed to use National Instruments output cards (6713 and 6534); uses shared clock for synchronization; "100 ns time resolution"; Cicero is GUI; component that interfaces with hardware is called Atticus; no support for closed-loop feedback or low-latency branching; last github commit 6 years ago, no commits to forks |
|LabView          | National Instruments               |  | Pretty much the current default option, with many ion trap groups using it.|
| QCoDeS|Delft|[github](https://github.com/QCoDeS/Qcodes)| | 

Other software control infrastructure for (quantum) science:

|Name              | Origin           | Link                             | Comment |
|-----             |----              |-----                             | ------  |
|Labber            |2015      |[labber.org](http://labber.org/) | Relies on 3rd party vendor's support for deterministic [timing](http://labber.org/online-doc/html/Measurement.html#hardware-timing-and-synchronization). No support for closed-loop feedback or low-latency branching. 
|QITKAT            | Oak Ridge | [DOI](http://spie.org/Publications/Journal/10.1117/1.OE.53.8.086103?SSO=1) | Software-defined quantum communication systems |
|ZIO| | | A software framework for Linux device drivers aimed at supporting controls and data acquisition hardware. ZIO supports sub-nanosecond timestamps, block-oriented input and output and transport of meta-data with the data samples.| 
| LabScript | | [labscriptsuite.org](http://labscriptsuite.org/) [DOI](https://aip.scitation.org/doi/10.1063/1.4817213) | |



Control system hardware (and related) for quantum information experiments.

|Name              |  Link                                      | Comment |
|-----                  |-----                                      |  ----       |
| Sinara            | [github](https://github.com/sinara-hw) | open source hardware for ARTIQ| 
|Quantum Labber (now Keysight)          |[website](https://www.keysight.com/us/en/products/software/application-sw/labber-software.html) | |
| quTAU | [qutau](http://www.qutools.com/quTAU/) | 8 channel, 81 ps TDC | 
|StelarIP| 4dsp.com | tool for combining gateware IP developed by 4dsp.com |
|Swabian Instruments | [swabianinstruments.com](http://swabianinstruments.com)|Mainly aimed at photonics|
|Raytheon BBN (now IBM)| [arXiv paper](https://arxiv.org/abs/1704.08314) | | 
| LiquidLab | [liquidinstruments.com](https://liquidinstruments.com)|Similar hardware to Stabilizer/Fast_Servo|
|Houke (Princeton) | [arxiv](https://arxiv.org/pdf/1703.00942.pdf) | |
|LabRAD hardware| [DOI](https://arxiv.org/abs/1507.03122) | |
|Easy Phi| [link](http://easy-phi.unige.ch) | no activity on github since 2014 |
|M-ACTION Hardware (ETH Zurich Ion Group)  | [Vlad's Thesis](https://www.research-collection.ethz.ch/bitstream/handle/20.500.11850/295923/Thesis_VNegnevitsky.pdf), [Mentioned in this thesis](https://quantumoptics.at/images/publications/diploma/MichaelMeth_Kontrolle_Laserimpulse_QIV.pdf) | Developed in the Home Lab at ETH Zurich.  Being adopted by Blatt lab at Innsbruck. |
|Zurich Instruments|[Website](https://www.zhinst.com)|They [propose here](https://www.zhinst.com/applications/quantumnano/trapped-ion) that their SC qubit hardware can be used for ion trapping.  No known users.  Per channel cost of their AWGs is probably too high to run a lab full of AOMs off.|
|CIQTEK| [website](https://www.ciqtek.com/en/products/5)|Chinese company producing quantum control hardware|
|Quantum Machines| [website](https://www.quantum-machines.co)|Israeli company producing quantum control hardware|