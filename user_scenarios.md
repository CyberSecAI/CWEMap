
# User Scenarios

## Key Phrases from Vulnerability Description 

### Background: 
Vulnerability Descriptions should use [Key Details Phrasing](https://www.cve.org/Resources/General/Key-Details-Phrasing.pdf) because _"the correct amount and type of information in a description is important"._

There are many use cases associated with using this Vulnerability Description:
1. Assigning other CVE data e.g. CWE, CPE, ....
2. Data Analysis and research to determine salient characteristics or trends 

Vulnerability Descriptions range significantly in quality, and there are even descriptions that have no vulnerability information.

### Narrative: 

#### Pre-Narrative (how things are now)

Where Key Phrases from Vulnerability Description are extracted, this tends to be done adhoc, in isolation, using a variety of tools from RegEx to Language Models.
This data is not publicly available or shared.


#### Post-Narrative (how we want things to be in the future - aspirational)

For all CVEs, the Key Phrases from Vulnerability Description are available in a repository that
1. is publicly available
2. is consistent format
3. allows feedback and updating
4. provides a rating of the quality of CVE Descriptions e.g. if a Vulnerability Description does not meet some minimum standard, then it is flagged.
5. is accurate i.e. the Key Phrases are correct for the Vulnerability Description

This increases the quality of Vulnerability Descriptions, and the associated data derived from them.


## Assign CWE

### Background: 


Per [CWE Guidance](https://cwe.mitre.org/documents/cwe_usage/guidance.html)
> Root cause mapping is the identification of the underlying cause(s) of a vulnerability. This is best done by correlating CVE Records and/or bug or vulnerability tickets with CWE entries. Today, this is not done accurately at scale by the vulnerability management ecosystem.
> 
> Accurate root cause mapping is valuable because it directly illuminates where investments, policy, and practices can address the root causes responsible for vulnerabilities so that they can be eliminated. This applies to both industry and government decision makers. Additionally, it enables:
> 1. Driving the removal of classes of vulnerabilities: Root cause mapping encourages a valuable feedback loop into a vendor’s SDLC or architecture design planning
> 2. Saving money: the more weaknesses avoided in your product development, the less vulnerabilities to manage after deployment
> 3. Trend analysis (e.g., how big of a problem is memory safety compared to other problems like injection)
> 4. Further insight to potential “exploitability” based on root cause (e.g., command injection vulnerabilities tend to see increased adversary attention, be targeted by certain actors)
> 5. Organizations demonstrating transparency to customers how they are targeting and tackling problems in their products


The [MITRE CWE (Common Weakness Enumeration) specification](https://cwe.mitre.org/) is a comprehensive list of software and hardware security vulnerabilities. It categorizes weaknesses to help identify and mitigate security flaws. The specification covers various types of weaknesses, from coding errors to design flaws. 

While it provides a clear framework, its complexity lies in the extensive classification system, the technical nature of vulnerabilities, and its depth, requiring detailed understanding of security, coding practices, and risk management to effectively use it.

There are ~~1000 CWEs, and the PDF version is almost 3000 pages.



### Narrative: 

#### Pre-Narrative (how things are now)
People struggle with the amount of information in [MITRE CWE](https://cwe.mitre.org/), and may not have the understanding of security required to assign CWEs.

Today, assigning CWEs is not done accurately at scale by the vulnerability management ecosystem. It is generally done manually.

#### Post-Narrative (how we want things to be in the future - aspirational)
Given a Vulnerability Description and related text (e.g. from bug or vulnerability references), the CWE(s) are automatically assigned with
1. the root cause and other weakness highlighted
2. the rationale for their choice including other CVE examples with similar weakness(es) and CWE assignment(s).
3. the chain of CWEs from root cause to follow on weaknesses



# User Story
## BULK_EXTRACT_KEYPHRASES
As any user, I want to assign KeyPhrases to CVE Descriptions in bulk automatically, so I can have the KeyPhrases for many/all CVE Descriptions.

## BULK_ASSIGN_CWES
As any user, I want to assign CWEs to CVE Descriptions in bulk automatically, so I can have the CWEs for many/all CVE Descriptions.

## BULK_CHECK_CWES
As any user, I want to check CWEs for CVE Descriptions in bulk automatically, so I can then assign the correct CWEs.

## INTERACTIVE_ASSIGN_CWES
As any user, I want to assign CWEs with the assistance of an expert on MITRE CWE specification, and security 
* to be able to get answers to my questions
* to get recommendations
* to be able to provide input and feedback to the expert

