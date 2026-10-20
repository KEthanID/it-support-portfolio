# Desktop RAM Boot Issue

**Setting:** HP Desktop IT Supervised Support Simulation - RAM Hardware Issue

## Issue

A user couldn't startup their Windows computer. The HP desktop would only power on for one second with an audible fan noise, then off for several seconds, while repeating this cycle endlessly.

## Investigation

An intermediate-level, internal evaluation was required to determine the exact cause. After an intensive search through the entire motherboard for any signs of changes and/or damage, it was discovered that one of the installed RAM modules was damaged.

## Approach used

Comparing the affected workstation with an operational one helped me shrink down the possibility of true PCB/PCH/Motherboard micro-hardware damage. The intermediate-level inspection that took place involved evaluating numerous installed modules, which included pin headers and micro-chipsets visually, without the usage of lens. The faulty RAM was located when my instructor asissted me in narrowing down the possibilities even further, since it is good to bear in mind that such damaged parts can cause these issues, without needing to go evaluate symptoms too far down initially.

## Result

After the faulty RAM was removed and the operational RAM was tested, the workstation started up normally into Windows after one pass, with no further issues being observed. I explained the change and asked the user to report any repeat of the problem.

## Skills in practice

CompTIA A+ concepts: internal hardware configuration, isolating a problem, and verifying a fix.

<details>
<summary>Framework connections</summary>

| Framework | Connection to this case |
| --- | --- |
| [DoD DCWF](../FRAMEWORK-MAPPINGS.md#dod-dcwf-ksa) | **222B:** removed a faulty RAM module that was preventing basic PC operation. **145A:** conducted an intermediate-level inspection of motherboard chipsets to verify no micro-damage present. |
| [NICE v2.0.0](../FRAMEWORK-MAPPINGS.md#nice-framework) | **K1090, S0488:** performed a micro-inspection of faulty RAM module with soldering scope and logged such for internal records; functional RAM module was also inspected and reseated into appropriate DIMM channel slot. |
| [NCAE-C](../FRAMEWORK-MAPPINGS.md#ncae-c-knowledge-units) | **IT Systems Components:** applied an understanding of a computer's hardware configuration. |

</details>