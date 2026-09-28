# Desktop disk boot error

**Setting:** HP BIOS, HBCD, and Hardware IT Supervised Support Simulation - Boot Error

## Issue

A user stated that their desktop failed to boot to Windows, despite several restarts. The PC would attempt to boot via a Win PXE but failed and would transfer to an external drive boot holding screen.

## Investigation

The HDD SATA data cable was disconnected. The HDD wasn't running, which pointed to a boot problem during startup.

## Approach Used

An initial investigation prompted a short, physical interior inspection after the HP BIOS of the desktop for the boot settings, as well as the HBCD via a USB for checking the BCD and partitions presented minimal results. A located SATA cable connection being disconnected in front of an internal HDD was a clue; with my instructor's guidance, I inspected and corrected the cable connection while following power-disconnection and static-safety precautions.

## Result

The HDD was detected and normal boot startup was observed on one pass. Succesful Windows desktop login was observed as well, with no symptoms of abnormal hardware performance.

## Skills in practice

CompTIA A+ concepts: BIOS troubleshooting, HBCD investigation, amd hardware examinations.

<details>
<summary>Framework connections</summary>

| Framework | Connection to this case |
| --- | --- |
| [DoD DCWF](../FRAMEWORK-MAPPINGS.md#dod-dcwf-ksa) | **222B:** used an understanding of computer operation to connect HDD behaivor with startup trouble. |
| [NICE v2.0.0](../FRAMEWORK-MAPPINGS.md#nice-framework) | **S0488, S0807:** maintained the system and used observed symptoms to solve a hardware problem. |
| [NCAE-C](../FRAMEWORK-MAPPINGS.md#ncae-c-knowledge-units) | **IT Systems Components:** connected the cooling system's role to reliable computer operation. |

</details>