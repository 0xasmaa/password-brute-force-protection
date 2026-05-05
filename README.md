
# Burp Turbo Intruder – Login Lockout Bypass Script

## Overview

This script is designed for use with [Burp Suite's Turbo Intruder](https://portswigger.net/bappstore/9abaa233088242e8be252cd4ff534988) extension. It performs a password brute-force attack against a login endpoint while bypassing account lockout mechanisms by interleaving valid "reset" login attempts between attack attempts.

---

## How It Works

- Loads a wordlist from `/usr/wordlist`
- Attempts each password against the target account (`carlos`)
- Every **2 attempts**, it sends a valid login with known credentials (`wiener:peter`) to **reset the lockout counter**
- All responses are logged to Turbo Intruder's results table

---

## Requirements

- Burp Suite Pro or Community
- **Turbo Intruder** extension installed (available via BApp Store)
- A wordlist file at `/usr/wordlist`
- A captured login HTTP request with `%s` placeholders for username and password

---

## Setup

1. Capture the login POST request in Burp Suite
2. Right-click the request → **Send to Turbo Intruder**
3. In the request, replace the username and password values with `%s`:
   ```
   username=%s&password=%s
   ```
4. Paste this script into the Turbo Intruder script editor
5. Adjust parameters as needed (see Configuration below)
6. Click **Attack**

---



---

## References

- [PortSwigger – Turbo Intruder](https://portswigger.net/research/turbo-intruder-embracing-the-billion-request-attack)
- [Web Security Academy – Brute Force Labs](https://portswigger.net/web-security/authentication/password-based)
