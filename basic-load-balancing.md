---

copyright:
  years: 2017, 2018, 2019
lastupdated: "2019-07-03"

keywords: basics, load balancing

subcollection: loadbalancer-service

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank_"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}

# Performing Load Balancer Basics
{: #ibm-cloud-load-balancer-basics}

The {{site.data.keyword.loadbalancer_full}} service distributes traffic among multiple server instances (bare metal and virtual server) that reside locally, within the same data center.

## Public to Private Load Balancer
{: #public-private-load-balancer}

A publicly accessible, fully qualified domain name is assigned to your load balancer service instance. You must use this domain name to access your applications hosted behind the load balancer service. This domain name may be registered with one or more public IP addresses. The public IP addresses and number of public IP addresses may change over time based on maintenance and scaling activities, which are transparent to the end users. The backend compute instances hosting your application must be on an IBM Cloud private network.

As a good practice, we recommended that you provision your backend servers as ‘private-only’, unless they require direct public connectivity. This practice helps achieve better security, and it preserves your public IP address. The applications hosted on these backend servers are still accessible over public network using the load balancer.
{: note}  

You may choose to allocate load balancer public IP addresses from either an IBM system pool(default) or a public VLAN under your account when creating your load balancer service instance.

## Private to Private Load Balancer
{: #private-private-load-balancer}

The internal load balancer is only accessible within the IBM Cloud private network.

Just like a public to private load balancer, your internal load balancer service instance is also assigned a fully qualified domain name. However, this domain name is registered with one or more private IP addresses.

Similar to a public load balancer, the private IP addresses and their numbers may change over time based on maintenance and scaling activities, which are transparent to end users.

The backend compute instances hosting your application must also be on the IBM Cloud private network.
{: note}

## Public to Public Load Balancer
{: #public-public-load-balancer}

The public to public load balancer is publicly accessible.

Just like other load balancer types, your public to public load balancer service instance is assigned a fully qualified domain name. This domain name may be registered with one or more public IP addresses.

Once the load balancer is provisioned, only public IP addresses of the members in the server tables context are visible. This is applicable for both Layer 4 and Layer 7 load balancer members.

The public IP addresses and their numbers may change over time based on maintenance and scaling activities, which are transparent to end users.

The backend compute instances hosting your application must be on the IBM Cloud public network.
{: note}

## Front-end and Back-end Application Ports/Protocols
{: #front-end-and-back-end-application-ports-protocols}

You may define up to ten front-end application ports (protocols) and map them to respective ports (protocols) on the back-end application servers. The fully qualified domain name assigned to your load balancer service instance and the front-end application ports are exposed to the external world. The incoming user requests are received on these ports.

On the other hand, the back-end ports are only known internally. These back-end ports may or may not be the same as the front-end ports. As an example, the load balancer may be configured to receive incoming web/HTTP traffic on front-end port 80, while the back-end servers are listening on custom port 81.

The supported front-end ports/protocols are HTTP, HTTPS and TCP. The supported back-end ports/protocols are also HTTP, HTTPS and TCP. Incoming HTTPS traffic must be terminated at the load balancer to allow for plain-text HTTP communication with the backend server. If the backend protocol is HTTPS, the traffic will be encrypted between load balancer and backend servers.

### Considerations
{: #considerations}

* During the initial configuration, you can define up to two front-end ports only. Once a load balancer is created, you can edit port configuration to define additional ports, up to the maximum of ten ports.
* All ten front-end ports must map to the same set of back-end server instances.
* The maximum number of server instances that may be placed behind a load balancer is 50.
* The port range of 56500 to 56520 is reserved for management purposes and cannot be used as front-end virtual ports.
* TCP port 56501 is used for management. If you choose to allocate load balancer public IP addresses from your public VLAN, please ensure that traffic to this management port as well as your application's ports are not blocked by any firewalls you may have deployed on your public VLANs. This is not required if you choose IBM system pool option to allocate load balancer public IP addresses.

## Load Balancing Methods
{: #load-balancing-methods}

The following three load balancing methods are available for distributing traffic among back-end application servers:

* **Round Robin:** Round Robin is the default load balancing method. With this method, the load balancer forwards incoming client connections in round-robin fashion to the back-end servers. As a result, all back-end servers receive roughly an equal number of client connections.

* **Weighted Round Robin:** With this method, the load balancer forwards incoming client connections to the back-end servers in proportion to the weight assigned to these servers. Each server is assigned a default weight of 50, which may be customized to any value between 0 and 100.

	As an example, if there are three application servers A, B and C, and their weights are customized to 60, 60 and 30 respectively, then servers A and B will receive an equal number of connections, while server C will receive half that number of connections.

	Re-setting a server weight to ‘0’ means no new connections will be forwarded to that server, but any existing traffic will continue to flow as long as it is active. Using a weight of ‘0’ can help bring down a server gracefully and remove it from service rotation.
	{: note}

	The server weight values are applicable only with the 'weighted round robin' method. They are ignored with 'round robin' and 'least connections' load balancing methods.
	{: note}

* **Least Connections:** With this method, the server instance serving the least number of connections at a given time receives the next client connection.

## Horizontal Scaling
{: #horizontal-scaling}

The load balancer adjusts its capacity automatically according to the load. When this occurs, you may see a change in the number of IP addresses associated with the load balancer's DNS name.
