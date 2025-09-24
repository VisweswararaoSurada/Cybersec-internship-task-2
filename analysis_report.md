# Phishing Email Analysis Report

**Analyzed file:** phishing_email_sample.txt  
**Date analyzed:** 2025-09-22

---

## 1. Summary
This email exhibits multiple phishing indicators: suspicious sender domain (typo-squatted), mismatched verification link, urgency language (24-hour deadline), and generic greeting. These traits indicate an attempt to trick the recipient into submitting credentials.

---

## 2. Sender Address & Spoofing
- **From header:** `support@paypa1.com` — note the `1` instead of `l` in "paypal". This is a common typo-squatting method.
- Recommendation: Do not trust the display name. Always check the real domain. If the domain is suspicious, do not interact with the email.

---

## 3. Header Analysis (what to check)
- Use an online header analyzer (e.g., MXToolbox Header Analyzer) or paste raw headers into a tool to check:
  - **Received:** track the hops and originating IP. If the originating IP is not from the email provider's mail servers, it's suspicious.
  - **SPF:** if SPF fails, sender is likely spoofed or sent from unauthorized host.
  - **DKIM:** missing or invalid DKIM signature is suspicious.
  - **DMARC:** DMARC policy helps determine if the message aligns with sender domain policy.
- *(Note: raw headers were not provided in the sample; if available, paste them into an analyzer for exact verification.)*

---

## 4. Links & Attachments
- Visible link: `http://secure-paypal.verify-account.example.com/verify?uid=8741`
  - The domain `verify-account.example.com` is not `paypal.com`. The true domain sits after "secure-paypal." which is a subdomain of `verify-account.example.com` — this is a deception technique.
  - **Hover strategy:** Hover (without clicking) to see actual URL. If the display text says "paypal.com" but the real link points elsewhere, it's phishing.
- No attachments in this sample. If attachments exist, do NOT open them. Scan with antivirus and inspect in a sandbox.

---

## 5. Social Engineering & Content Checks
- **Urgency:** "verify within 24 hours" — pushes victim to act quickly without thinking.
- **Generic greeting:** "Dear Customer" — legitimate services often use your real name.
- **Tone:** Threat of suspension is used to trigger fear.
- **Grammar/spelling:** Example uses "PayPal" misspelt in the sender address; grammar is plain but the domain misspelling is the main clue.

---

## 6. Risk Level
- **High** — links are deceptive and the message attempts credential theft.

---

## 7. Recommended Actions
1. Do not click links or open attachments.  
2. Report the email to your organization's SOC or to the legitimate service (e.g., PayPal's phishing report address).  
3. Mark the email as phishing in your email client.  
4. If any credentials were entered, change the account password immediately, enable MFA, and check account activity.  
5. Preserve headers and forward the email to security/contact addresses for investigation.

---

## 8. Additional Notes / Tools to Use
- **Header analyzers:** MXToolbox (Header Analyzer), Google’s message header viewer (Gmail: "Show original"), or other forensic tools.  
- **URL checking:** VirusTotal URL scan, URLVoid, or simply examine domain parts carefully.  
- **SPF/DKIM/DMARC checks:** Use online SPF/DKIM checkers or the header analyzer for results.

---

## 9. Conclusion
This sample is a straightforward credential harvesting phishing attempt using a typo-squatted domain and urgency. Proper verification of sender domain and header checks would expose these signs. Practicing safe handling (report, do not click, preserve evidence) is essential.
