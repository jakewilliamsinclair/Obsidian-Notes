# Certificates
## PGP
More than just a certificate system
## X.509

## Revocation
### X.509
Certificates Revocation List (CRL) - list of revoked certificates.
Uses On-Line Certificate Status Protocol (OCSP)
### PGP
Each signer revokes their signature.
# Cipher Suites
Key Exchange
Digital Signature
Bulk Encryption
Message Authentication Code
# Certificate Authority Setup
Generate public/private key pair
Create X.509 certificate
We assume it is a root CA so it signs itself.
# Firewalls, Tunnelling, VPNs and IDS/IPS
## Firewalls
One of the first lines of defence that monitors incoming and outgoing traffic based on predetermined rules.
In general firewalls will deny or allow packets based on their rules
### Firewall Rules
#### Priority
Determines the order in which the rules are applied.
#### Time
Rules can be set during scheduled times.
#### Context
Based on context, e.g. whether a laptop is on-site or remote.
### Note
Older firewalls had each rule as a separate instruction like an IF-ELSE-THEN, meaning the order mattered a lot.
### Stateless vs Stateful
#### Stateless
Stores nothing, simply follows the rules in the moment.
"Packet by packet"
#### Stateful
Stores information that is used in the application of rules.
## Tunnelling
Data can be sent through a "tunnel", keeping it safe and encrypted throughout transmission across a public network.
### TLS VPN
Secure protocol for protecting specific info
Layers 4-7
### IPSec
Set of protocols for all IP traffic by encrypting packets
Layer 3