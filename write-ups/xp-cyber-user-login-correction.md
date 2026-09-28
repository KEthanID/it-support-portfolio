# XP Cyber: Helpdesk Fun: User Login Nightmares

**Setting:** XP Cyber Challenge simulation

## Issue

I worked through a simulated help-desk inquiry involving a login issue. User needed help with account access, specifically regarding his Windows 11 workstation.

## Investigation

This report affected only one user with one virtual machine workstation. The investigation found that the workstation was not added as an object within the server Active Directory.

## Approach used

I used the ticket's urgency to organize the work and execute efficiency in a timely manner. Distinguishing connectivity for the domain controller helped me narrow the network issues. Evaluating the Server Active Directory for the virtual workstation assisted me further in determing if this was a result of an object misconfiguration error. Test-ComputerSecureChannel was also used within an Admin PowerShell Terminal, with the parameters -Repair and -Verbose to repair the channel as finalization of the error.

## Result

I addressed the access and connectivity requests and recorded the outcomes. My takeaway was to pair a technical correction with a clear explanation of what changed and whether the requested function works.

## Skills in practice

CompTIA A+ concepts: Service-desk communication, Network troubleshooting, and Windows administration.

<details>
<summary>Framework connections</summary>

| Framework | Connection to this case |
| --- | --- |
| [DoD DCWF](../FRAMEWORK-MAPPINGS.md#dod-dcwf-ksa) | **6010:** described issues and outcomes in tickets. **3513:** applied Windows and Linux administration concepts. |
| [NICE v2.0.0](../FRAMEWORK-MAPPINGS.md#nice-framework) | **K0903, S0478:** organized service-desk work and responded to support requests. **K0983:** used networking principles to distinguish connectivity for domain controller. |
| [NCAE-C](../FRAMEWORK-MAPPINGS.md#ncae-c-knowledge-units) | **Network Technology and Protocols:** considered packet loss for domain controller. **Operating Systems Administration:** worked with access and configuration across Windows. |

</details>