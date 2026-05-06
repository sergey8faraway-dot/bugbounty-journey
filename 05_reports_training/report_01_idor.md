## IDOR in transcript download endpoint allows unauthorized access to other users' chat logs

### 1) Overview

#### Title
IDOR in transcript download endpoint allows unauthorized access to other users' chat logs

#### Summary
I intercepted a request to `POST /download-transcript` in Burp Suite. The response contained `Location: /download-transcript/12.txt`, which exposed a direct object reference.

### 2) Reproduction

#### Steps to Reproduce
1. Intercept `POST /download-transcript` in Burp Suite.
2. Observe `Location: /download-transcript/12.txt` in the response.
3. Request another transcript filename (for example, change `12.txt` to `1.txt`).
4. Receive another user's chat transcript without authorization.

#### Evidence
- `Location: /download-transcript/12.txt` reveals the transcript object reference.
- Changing the transcript filename returns a different user's private chat log.
- The server returns sensitive transcript data without enforcing authorization checks.

### 3) Risk & Fix

#### Impact
An attacker can read private transcripts and obtain credentials, which can lead to account takeover.

#### Recommendation
Enforce server-side object-level authorization checks for every transcript request.
