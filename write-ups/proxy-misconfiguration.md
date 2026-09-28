# Websites loading faults

**Setting:** Windows 11 IT Supervised Support Simulation - Website Connection Errors

## Issue

A user stated that their laptop was connected to the network, but was unable to access any websites from several attempts. Network symbol indicated no initial errors.

## Investigation

An misconfigured proxy setting was directing browser traffic through an unavailable local proxy, preventing normal web access even though the workstation remained connected to the network.

## Approach used

I separated basic network access from the browser-specific web access. The browser’s proxy error shifted the investigation away from DNS and toward Windows proxy configuration; with supervisor guidance, I confirmed an unexpected proxy setting and corrected it.

## Result

I opened several websites that hadn't loaded before; both worked after the change. This reminded me to examine symptoms further with simpler, evidence-supported troubleshooting steps rather than attempting to jump to complex-level exmainations of severe symptoms with terminal usage.

## Skills in practice

CompTIA A+ concepts: network troubleshooting, DNS checks, and proxy settings.

<details>
<summary>Framework connections</summary>

| Framework | Connection to this case |
| --- | --- |
| [DoD DCWF](../FRAMEWORK-MAPPINGS.md#dod-dcwf-ksa) | **22:** used networking concepts to distinguish connectivity, name lookup, and browser behavior. |
| [NICE v2.0.0](../FRAMEWORK-MAPPINGS.md#nice-framework) | **K0983, S0661:** applied networking principles to troubleshoot a client problem. |
| [NCAE-C](../FRAMEWORK-MAPPINGS.md#ncae-c-knowledge-units) | **Basic Networking:** distinguished a network connection from a working application connection. |

</details>