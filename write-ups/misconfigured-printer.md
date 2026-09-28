# Printer .PRN issue

**Setting:** Windows 11 IT Supervised Support Simulation - Printer Port Issue

## Issue

A user couldn't print from their Windows computer. The printer appeared online, with no errors being reported from numerous terminal reports.

## Investigation

The affected computer used a different printer connection setting, called a port. That setting wasn't working for this printer, since it was found that 2 print-to-file functions were causing an .PRN overwrite issue.

## Approach used

Comparing the affected computer with a working one helped me narrow the issue to a local setting. I checked for stuck jobs and configuration differences instead of assuming the printer itself had failed. My instructor confirmed the expected configuration, and I corrected the connection setting.

## Result

The printer showed as ready and a test page printed successfully from the affected computer. I explained the change and asked the user to report any repeat of the problem.

## Skills in practice

CompTIA A+ concepts: printer configuration, isolating a problem, and verifying a fix.

<details>
<summary>Framework connections</summary>

| Framework | Connection to this case |
| --- | --- |
| [DoD DCWF](../FRAMEWORK-MAPPINGS.md#dod-dcwf-ksa) | **221A:** corrected a peripheral configuration to the approved setting and tested it. |
| [NICE v2.0.0](../FRAMEWORK-MAPPINGS.md#nice-framework) | **S0679, S0680:** configured the printer connection and validated it with a test page. |
| [NCAE-C](../FRAMEWORK-MAPPINGS.md#ncae-c-knowledge-units) | **IT Systems Components:** applied an understanding of a computer's peripheral configuration. |

</details>