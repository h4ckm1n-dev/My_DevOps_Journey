###   Cert Manager

[Cert Manager](https://cert-manager.io/) is an open-source certificate management solution for Kubernetes. It automates the management and issuance of TLS certificates, making it easier to secure your applications and services running on Kubernetes.

Here are some key features and concepts related to Cert Manager:

#### Certificate Issuers

Cert Manager supports multiple certificate issuers, including Let's Encrypt, self-signed certificates, and custom certificate authorities (CAs). These issuers are responsible for generating and signing the TLS certificates used to secure your applications.

Let's Encrypt is a popular option that offers free TLS certificates. By configuring Cert Manager with Let's Encrypt issuer, you can automatically obtain and renew TLS certificates for your domains without manual intervention.

#### Certificate Requests and Orders

In Cert Manager, you define Certificate Requests to specify the details of the desired certificate, such as the common name, subject alternative names (SANs), and the issuer to use. A Certificate Request is submitted to Cert Manager, which then interacts with the configured issuer to obtain the corresponding certificate.

Certificate Orders represent the ongoing process of obtaining a certificate from an issuer. Cert Manager manages the lifecycle of the Order, ensuring that the certificate is obtained, stored, and renewed as necessary.

#### Certificate Controllers

Cert Manager employs controllers that run within your Kubernetes cluster to manage the lifecycle of certificates. These controllers watch for changes in Certificate Requests and Orders, and they interact with the appropriate issuer to fulfill the certificate issuance process.

#### Certificate Stores

Cert Manager provides a Certificate Store functionality that allows you to automatically inject certificates into Kubernetes resources, such as Ingress controllers or other workloads. This feature simplifies the process of using the obtained certificates within your applications, eliminating the need for manual certificate management.

#### Automatic Certificate Renewal

Cert Manager includes an automatic certificate renewal mechanism, ensuring that your TLS certificates are always up to date. It monitors the expiration date of the certificates and initiates the renewal process when necessary. This automated renewal process helps you maintain the security of your applications without manual intervention.

#### Integration with Kubernetes Ingress

Cert Manager integrates seamlessly with Kubernetes Ingress resources. By annotating your Ingress resources with the appropriate annotations, Cert Manager can automatically provision and manage TLS certificates for your Ingress endpoints. This enables secure HTTPS communication for your applications without the need for manual certificate configuration.

#### Customization and Advanced Configuration

Cert Manager provides extensive customization options and advanced configuration capabilities. You can define custom certificate templates, configure specific certificate renewal intervals, and tailor the behavior of the certificate issuance and renewal processes according to your requirements.

#### Monitoring and Logging

Cert Manager generates logs that provide visibility into the certificate management operations, including certificate issuance, renewal, and errors. Monitoring these logs helps you ensure the proper functioning of the certificate management process and troubleshoot any issues that may arise.

Cert Manager's integration with Kubernetes and its automation capabilities simplify the management of TLS certificates for your applications. By leveraging Cert Manager, you can ensure secure and encrypted communication within your Kubernetes cluster and with external services.

---
## Self-Signed Certificates
1. Create a self-signed CA ([[ssl-certs]]) creating a ca.key (private-key) and ca.crt (certificate)

(ca.key)
```bash
openssl genrsa -out ca.key 4096
```

(ca.crt)
```bash
openssl req -new -x509 -sha256 -days 365 -key ca.key -out ca.crt
```

2. Convert the files to a one line base64 decoded string (only works on Linux base64 tool)
```bash
cat ca.key | base64 -w 0
```

3. Create a new ssl secret object using the strings
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: ssl-issuer-secret
  # (Optional) Metadata
  # ---
  # namespace: your-namespace
type: Opaque
data:
  tls.crt: <base64-decoded-string>
  tls.key: <base64-decoded-string>
```

4. Create a new ClusterIssuer or Issuer object by using the ssl secret
```yaml
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: selfsigned-issuer
  # (Optional) Metadata
  # ---
  # namespace: your-namespace
spec:
  ca:
    secretName: ssl-issuer-secret
```

