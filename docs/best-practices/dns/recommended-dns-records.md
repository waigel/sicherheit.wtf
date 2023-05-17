---
description: Recommended DNS Records
---

# SPF, DMARC & DKIM without sending E-Mails

Domains that do not send emails can still be used in email spoofing or phishing attacks.
To prevent this, at least the following DNS records should also be set for domains without active e-mail dispatch.

| Name | Type | FQDN | Value | Description |
| ----- | --- | -- | --- | -- | 
| SPF |  `<domain>.<tld>` | `TXT` | `v=spf1 -all`  | There are no authorized IP addresses that send emails for this domain. |
| DKIM | `*._domainkey.<domain>.<tld>` | `TXT` | `v=DKIM1; p=` | There is no public key with which received DKIM signatures can be verified. |
| DMARC | `_dmarc.<domain>.<tld>` | `TXT` | `v=DMARC1;p=reject;adkim=s;aspf=s` | SPF and DKIM should be evaluated for all subdomains. If either SPF or DKIM fails, it is recommended to reject the received email. |

## Sources

- https://www.cloudflare.com/learning/dns/dns-records/protect-domains-without-email/