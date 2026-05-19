1. Raw IP Address (has_ip) — 30 pts
Legitimate sites use domain names. Phishing sites often use bare IPs like http://192.168.1.1/login to avoid domain registration trails. Detected with a regex: \d{1,3}(\.\d{1,3}){3}.
2. @ Symbol (has_at_symbol) — 25 pts
Browsers ignore everything before @ in a URL. So http://google.com@evil.com actually goes to evil.com. A classic phishing trick.
3. Excessive Subdomains (excess_subdomains) — 20 pts
Phishers use deep subdomains to fake legitimacy: paypal.secure.login.evil.com. Three or more dots in the domain triggers this flag.
4. No HTTPS (no_https) — 20 pts
Legitimate modern sites almost universally use HTTPS. A plain http:// URL is a significant red flag for credential-harvesting pages.
5. URL Shortener (is_shortened) — 20 pts
Services like bit.ly or tinyurl.com hide the real destination. Phishers use them to obscure malicious domains.
6. Suspicious Keywords (suspicious_keywords) — up to 8 pts each
Words like login, verify, secure, paypal, password, confirm are disproportionately common in phishing URLs. Each match adds points; two or more triggers a higher penalty.
7. Long URL (long_url) — 10 pts
Phishing URLs often pad the address with fake-looking paths to seem legitimate (e.g. /secure/account/verify/update/step2). Over 75 characters triggers this.
8. Hyphen in Domain (hyphen_in_domain) — 10 pts
Real brands rarely use hyphens in their core domain. paypal-secure.com is a textbook phishing pattern.
9. Double Slash Redirect (double_slash_redirect) — 15 pts
A // appearing after the protocol section can redirect browsers to a completely different host.
10. Hex/Percent Encoding (hex_encoding) — 10 pts
Encoding characters as %XX (e.g. %2F for /) can disguise malicious URLs from both users and basic scanners.
11. Too Many Dots (many_dots) — 15 pts
More than 4 dots in the full URL often signals subdomain abuse or obfuscated paths
