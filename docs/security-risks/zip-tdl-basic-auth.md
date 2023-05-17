---
description: Increased risk of domain spoofing with .Zip TDL
---
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# Domain spoofing with .Zip TDL

| Category            | Severity |  Description |
| ------------------- | -------- | ------ |
| Phishing & Malware  | Medium     | It can be difficult to detect domain spoofing in download URLs |


# Introduction

Google launched a new TLD or “Top Level Domain” of .zip, the security community immediately raised flags about the potential dangers of this TLD.

## Issue

A detailed explanation can be found here: https://medium.com/@bobbyrsec/the-dangers-of-googles-zip-tld-5e1e675e59a5

In summary, attackers can create easily confused download urls using the basic auth embed synatx. 

For example: 

- [https://github.com∕kubernetes∕kubernetes∕archive∕refs∕tags∕@v1271.zip](https://github.com∕kubernetes∕kubernetes∕archive∕refs∕tags∕@v1271.zip)
- [https://github.com/kubernetes/kubernetes/archive/refs/tags/v1.27.1.zip](https://github.com/kubernetes/kubernetes/archive/refs/tags/v1.27.1.zip)

These domains can only be distinguished from each other if you look very closely and know about basic auth.

![](/img/docs/2023-05-17_21-59.png)
*Source: https://cv.jeyrey.net/img?equivocal-urls*

Therefore, there is an increased risk of domain spoofing.

---


## Advisable action

- Look for domains containing U+2044 (⁄) and U+2215 (∕)
- Look for domains containing @ operators followed by .zip files
- Always be careful about downloading files from URLs sent by unknown recipients, and hover over URLs before clicking to see the expanded URL path

It is advisable to stop resolving the .zip TLD locally or at the router level. This way, a possible domain spoofing attack cannot be carried out.

<Tabs>
  <TabItem value="linux" label="Linux" default>
    <ul>
    <li>1. Edit your <code>/etc/hosts</code></li>
    <li>2. Add the following line <code>0.0.0.0 .zip</code><br/>
        To route all traffic based on this TDL to void.</li>
    <li> 3. Clear your DNS cache</li>
    </ul>
  </TabItem>
</Tabs>


## Sources
- https://www.registry.google/announcements/launch-details-for-eight-new-tlds/
- https://medium.com/@bobbyrsec/the-dangers-of-googles-zip-tld-5e1e675e59a5