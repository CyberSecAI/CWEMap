<div align="center">

<h4><code>extract_key_entities</code> is a prompt that <em>extracts key named entities</em> i.e. Named Entity Recognition from a vulnerability description.</h4>

</div>

<br />

## Description

**`extract_key_entities` addresses the problem of confusion regarding a weakness versus an impact in a vulnerability descriptions.**

This prompt _extract_key_entities_ supports the following features:

- Extracts Key Details Phrasing (aka Named Entities) from Vulnerability Descriptions using the KeyEntities provided.
- Specify the ROOT CAUSE WEAKNESS and other WEAKNESS

## Examples

The N-Shot examples in [system.md](system.md) with heading "Example Synthetic" were generated by Claude Sonnet 3.5 

Claude Sonnet 3.5 was used for these examples below.


### CVE-2021-4206
"A flaw was found in the QXL display device emulation in QEMU. An integer overflow in the cursor_alloc() function can lead to the allocation of a small cursor object followed by a subsequent heap-based buffer overflow. This flaw allows a malicious privileged guest user to crash the QEMU process on the host or potentially execute arbitrary code within the context of the QEMU process."Certainly. I'll extract the KeyEntities from the provided vulnerability description following the guidelines and examples given. Here's the analysis:

````
===KeyEntities===
[COMPONENT] QXL display device emulation
[PRODUCT] QEMU
[VERSION]
[ROOTCAUSE] integer overflow
[WEAKNESS] heap-based buffer overflow
[ATTACKER] a malicious privileged guest user
[IMPACT] crash the QEMU process on the host or potentially execute arbitrary code within the context of the QEMU process
[VECTOR] the cursor_alloc() function
Note: The description doesn't explicitly mention a vendor or specific version, so those fields are left blank. The weakness is identified as an integer overflow, which leads to a heap-based buffer overflow, but I've listed the primary weakness as the integer overflow since it's the root cause.
````

### CVE-2021-21939 

A heap-based buffer overflow vulnerability exists in the XWD parser functionality of Accusoft ImageGear 19.10. A specially-crafted file can lead to code execution. An attacker can provide a malicious file to trigger this vulnerability.

````
I'll extract the KeyEntities from the provided vulnerability description following the guidelines and examples given:
===KeyEntities===
[COMPONENT] XWD parser functionality
[VENDOR] Accusoft
[PRODUCT] ImageGear
[VERSION] 19.10
[WEAKNESS] heap-based buffer overflow
[ATTACKER] An attacker
[IMPACT] code execution
[VECTOR] a specially-crafted file
````

### CVE-2022-20906
Multiple vulnerabilities in Cisco Nexus Dashboard could allow an authenticated, local attacker to elevate privileges on an affected device. These vulnerabilities are due to insufficient input validation during CLI command execution on an affected device. An attacker could exploit these vulnerabilities by authenticating as the rescue-user and executing vulnerable CLI commands using a malicious payload. A successful exploit could allow the attacker to elevate privileges to root on an affected device.

````
I'll extract the KeyEntities from the provided vulnerability description following the guidelines and examples given:
===KeyEntities===
[COMPONENT] CLI command execution
[VENDOR] Cisco
[PRODUCT] Nexus Dashboard
[VERSION]
[WEAKNESS] insufficient input validation
[ATTACKER] an authenticated, local attacker
[IMPACT] elevate privileges to root
[VECTOR] authenticating as the rescue-user and executing vulnerable CLI commands using a malicious payload
Note: The description mentions "Multiple vulnerabilities" but doesn't specify the exact number or types. I've focused on the common elements described for these vulnerabilities.
````

### CVE-2022-4125

The Popup Manager WordPress plugin through 1.6.6 does not have authorisation and CSRF check when creating/updating popups, and is missing sanitisation as well as escaping, which could allow unauthenticated attackers to create arbitrary popups and add Stored XSS payloads as well

````
I'll extract the KeyEntities from the provided vulnerability description following the guidelines and examples given:
===KeyEntities===
[PRODUCT] Popup Manager WordPress plugin
[VERSION] through 1.6.6
[WEAKNESS] does not have authorisation and CSRF check, missing sanitisation as well as escaping
[ATTACKER] unauthenticated attackers
[IMPACT] create arbitrary popups and add Stored XSS payloads
[VECTOR] creating/updating popups
[COMPONENT] popup creation/update functionality
Note: The description doesn't mention a specific vendor other than it being a WordPress plugin. The weakness is compound, including lack of authorization, CSRF checks, and missing sanitization/escaping.
````

### CVE-2022-31748 Very little vulnerability info

CVE Description
Mozilla developers Gabriele Svelto, Timothy Nikkel, Randell Jesup, Jon Coppeard, and the Mozilla Fuzzing Team reported memory safety bugs present in Firefox 100. Some of these bugs showed evidence of memory corruption and we presume that with enough effort some of these could have been exploited to run arbitrary code. This vulnerability affects Firefox < 101.

I'll extract the KeyEntities from the provided vulnerability description following the guidelines and examples given:

````
===KeyEntities===
[PRODUCT] Firefox
[VERSION] < 101
[WEAKNESS] memory safety bugs
[ATTACKER]
[IMPACT] run arbitrary code
[VECTOR]
[COMPONENT]
````

Note: This description is somewhat different from the typical vulnerability reports we've seen before. It doesn't explicitly mention an attacker or attack vector. The impact is presumed rather than definitively stated. I've included the information that is available and left some fields blank where the description doesn't provide specific details.


### Bogus Example

"i burnt my banana bread in the oven due to being distracted and that resulted in a denial of service and arbitrary code execution"

````
I appreciate your creative example! While it's not a real software vulnerability, I can play along and extract the key entities as if it were one, following the format we've been using. Here's a lighthearted interpretation:
===KeyEntities===
[PRODUCT] Banana Bread
[VERSION]
[WEAKNESS] lack of attention (being distracted)
[ATTACKER] the cook (self)
[IMPACT] denial of service and arbitrary code execution
[VECTOR] leaving bread in the oven for too long
[COMPONENT] oven
Note: This isn't a genuine software or hardware vulnerability, but rather a humorous analogy. In reality, "denial of service" here could be interpreted as the bread being inedible, and "arbitrary code execution" might humorously refer to unexpected results in the kitchen. Always remember to set timers when baking to avoid such "vulnerabilities" in your culinary endeavors!
````

## References

1. https://www.cve.org/Resources/General/Key-Details-Phrasing.pdf
2. https://cwe.mitre.org/documents/cwe_usage/guidance.html
3. https://github.com/tricktreat/PromptNER
4. https://academic.oup.com/jamia/article/31/9/1812/7590607?login=false Improving large language models for clinical named entity recognition via prompt engineering 