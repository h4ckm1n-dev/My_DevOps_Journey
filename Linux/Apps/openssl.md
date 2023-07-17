# OpenSSL Cheat-Sheet

OpenSSL is an open-source cryptographic library that provides various cryptographic functions and tools for secure communication, encryption, and certificate management. It is widely used in many applications and systems for implementing secure protocols, generating certificates, and performing cryptographic operations. Here are some common use cases and commands for OpenSSL

## Generating Keys and Certificates

COMMAND | DESCRIPTION
---|---
`openssl genrsa -out private.key 2048` | Generate a 2048-bit RSA private key
`openssl req -new -key private.key -out csr.csr` | Generate a certificate signing request (CSR) using the private key
`openssl req -x509 -sha256 -key private.key -in csr.csr -out certificate.crt -days 365` | Generate a self-signed certificate using the private key and CSR
`openssl rsa -in private.key -out new_private.key` | Convert a private key to a different format or remove the passphrase

## Certificate Signing and Verification

COMMAND | DESCRIPTION
---|---
`openssl ca -in csr.csr -out signed.crt -cert ca.crt -keyfile ca.key` | Sign a certificate signing request (CSR) using a certificate authority (CA) key and certificate
`openssl x509 -in certificate.crt -text -noout` | Display detailed information about a certificate
`openssl verify -CAfile ca.crt certificate.crt` | Verify the validity of a certificate using a CA certificate
`openssl crl2pkcs7 -nocrl -certfile certificate.crt -out certificate.p7b` | Convert a certificate to PKCS#7 format

## Encryption and Decryption

COMMAND | DESCRIPTION
---|---
`openssl enc -aes256 -in plaintext.txt -out encrypted.txt -pass pass:<password>` | Encrypt a file using AES-256
`openssl enc -aes256 -d -in encrypted.txt -out decrypted.txt -pass pass:<password>` | Decrypt an encrypted file using AES-256

## Message Digests

COMMAND | DESCRIPTION
---|---
`openssl dgst -sha256 file.txt` | Calculate the SHA-256 hash of a file
`openssl dgst -md5 file.txt` | Calculate the MD5 hash of a file

## SSL/TLS Testing

COMMAND | DESCRIPTION
---|---
`openssl s_client -connect host:port` | Connect to an SSL/TLS server and print the certificate and handshake details
`openssl s_server -accept port -cert certificate.crt -key private.key` | Start an SSL/TLS server using a certificate and private key

## Miscellaneous

COMMAND | DESCRIPTION
---|---
`openssl version` | Display the OpenSSL version information
`openssl rand -hex 16` | Generate a random hexadecimal string
`openssl rand -base64 32` | Generate a random base64-encoded string

