Overview
This script is designed for use with Burp Suite's Turbo Intruder extension. It performs a password brute-force attack against a login endpoint while bypassing account lockout mechanisms by interleaving valid "reset" login attempts between attack attempts.


How It Works

Loads a wordlist from /usr/wordlist
Attempts each password against the target account (carlos)
Every 2 attempts, it sends a valid login with known credentials (wiener:peter) to reset the lockout counter
All responses are logged to Turbo Intruder's results table


Requirements

Burp Suite Pro or Community
Turbo Intruder extension installed (available via BApp Store)
A wordlist file at /usr/wordlist
A captured login HTTP request with %s placeholders for username and password


