# Certutil Cheat-Sheet

Cert Utils refers to a collection of utility tools and commands used for working with X.509 digital certificates. These tools provide functionalities such as certificate generation, management, inspection, and validation. Here are some common cert utils and their purposes:

1. OpenSSL: OpenSSL is a widely used open-source toolkit that provides a set of tools and libraries for secure communication using SSL/TLS protocols. It includes commands for generating and managing certificates, private keys, and certificate signing requests (CSRs). OpenSSL commands can also be used for certificate validation, conversion, and inspection.
    
    Example commands:
    
    - `openssl genrsa` - Generate a new RSA private key.
    - `openssl req` - Generate a certificate signing request (CSR) for a new certificate.
    - `openssl x509` - Display or manipulate X.509 certificate files.
    - `openssl pkcs12` - Create or manipulate PKCS#12 files (container format for certificates and private keys).
2. Keytool: Keytool is a command-line tool provided by the Java Development Kit (JDK) for managing Java KeyStore (JKS) files. It is primarily used for managing digital certificates and private keys used in Java-based applications. Keytool can generate self-signed certificates, import and export certificates, and manage certificate trust chains.
    
    Example commands:
    
    - `keytool -genkeypair` - Generate a new key pair and self-signed certificate.
    - `keytool -importcert` - Import a certificate into a keystore.
    - `keytool -exportcert` - Export a certificate from a keystore.
3. CFSSL: CFSSL (CloudFlare's PKI toolkit) is a set of tools and libraries for working with digital certificates and certificate authorities (CAs). It provides functionalities for certificate signing, certificate bundling, and certificate revocation list (CRL) generation. CFSSL is commonly used in the context of building and managing public key infrastructures (PKIs).
    
    Example commands:
    
    - `cfssl genkey` - Generate a new private key and certificate signing request (CSR).
    - `cfssl sign` - Sign a certificate using a CA certificate and key.
    - `cfssl bundle` - Bundle multiple certificates into a single file.
4. Certbot: Certbot is a command-line tool for automatically obtaining and renewing SSL/TLS certificates from Let's Encrypt, a free and open Certificate Authority (CA). It simplifies the process of obtaining and managing TLS certificates for web servers. Certbot supports various web server platforms and can automate the configuration and installation of certificates.
    
    Example commands:
    
    - `certbot certonly` - Obtain a new certificate from Let's Encrypt.
    - `certbot renew` - Renew existing certificates.

These are just a few examples of cert utils available. Different tools may have different features and capabilities depending on the specific use case and requirements. It's important to refer to the documentation and usage guides of each tool to understand their full capabilities and usage.

## General Operations

COMMAND | DESCRIPTION
---|---
`certutil -?` | Display the command-line help for certutil
`certutil -v -?` | Display detailed command-line help for certutil
`certutil -dump` | Dump the contents of a certificate file
`certutil -addstore storename certfile` | Add a certificate to a specified certificate store
`certutil -delstore storename certid` | Delete a certificate from a specified certificate store

## Certificate Store Operations

COMMAND | DESCRIPTION
---|---
`certutil -store storename` | List all certificates in a specified certificate store
`certutil -store -user storename` | List all user-specific certificates in a specified certificate store
`certutil -store -enterprise storename` | List all enterprise-specific certificates in a specified certificate store
`certutil -store -enterprise -user storename` | List all enterprise/user-specific certificates in a specified certificate store

## Certificate Verification and Validation

COMMAND | DESCRIPTION
---|---
`certutil -verify certfile` | Verify the signature on a certificate
`certutil -f -urlfetch -verify certfile` | Verify the signature on a certificate using URL fetch for certificate revocation checking
`certutil -url certfile` | Retrieve and display information about the certificate from its associated URL

## Exporting and Importing Certificates

COMMAND | DESCRIPTION
---|---
`certutil -exportPFX certid pfxfile` | Export a certificate with its private key as a PFX file
`certutil -importPFX pfxfile` | Import a certificate with its private key from a PFX file
`certutil -importcert certfile` | Import a certificate from a certificate file
`certutil -importCRL crlfile` | Import a certificate revocation list (CRL) from a file
`certutil -repairstore storename certid` | Repair a certificate chain in a specified certificate store

## Other Operations

COMMAND | DESCRIPTION
---|---
`certutil -addstore -f -enterprise storename certfile` | Forcefully add a certificate to an enterprise-specific certificate store
`certutil -csp -addprovider providername` | Add a cryptographic service provider (CSP) to the registry
`certutil -renewCert <CertId>` | Renew a certificate with a new key pair and signing request
`certutil -dspublish -f filename` | Publish a certificate and CRL to a specified location

