---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-12"

keywords: ssl, offload, cipher, suite

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank_"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# SSL Offload with IBM Cloud Load Balancer
{: #ssl-offload-with-ibm-cloud-load-balancer}

For all incoming HTTPS connections, the load balancer service terminates the SSL connection and establishes a plain-text HTTP communication with the back-end server. CPU-intensive SSL handshakes and encryption/decryption tasks are shifted away from the back-end servers, allowing them to use all their CPU cycles for processing application traffic.

An SSL certificate is required for the load balancer to perform SSL offload tasks. You may use a pre-existing SSL certificate or purchase a new one, and manage it through the [IBM© Cloud Certificate Store ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/classic/security/sslcerts){:new_window}.

## SSL Cipher Suites
{: #ssl-cipher-suites}

The load balancer service supports TLS version 1.2 with SSL offload.

The following SSL ciphers are supported by your load balancer:

* ECDHE-RSA-AES256-GCM-SHA384
* ECDHE-RSA-AES256-SHA384
* AES256-GCM-SHA384
* AES256-SHA256
* ECDHE-RSA-AES128-GCM-SHA256
* ECDHE-RSA-AES128-SHA256
* AES128-GCM-SHA256
* AES128-SHA256

If your load balancer has one or more HTTPS front-end application ports (protocols) configured, by default all the above predefined SSL ciphers will be enabled for your load balancer.

You can choose to enable different SSL ciphers for your load balancer if needed. For more information, refer to [Choose a preferred cipher suite for your HTTPS application](/docs/loadbalancer-service?topic=loadbalancer-service-choosing-a-preferred-cipher-suite-for-your-https-application).
{: note}
