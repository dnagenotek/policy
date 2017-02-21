# Introduction

DNA Genotek Inc ("DNA Genotek") is committed to ensuring the confidentiality, privacy, integrity, and availability of all electronic protected health information (ePHI) it receives, maintains, processes and/or transmits on behalf of its Customers. As providers of compliant, hosted software as a service used by health technology businesses and academic researchers, DNA Genotek strives to maintain compliance, proactively address information security, mitigate risk for its Customers, and assure known breaches are completely and effectively communicated in a timely manner. The following documents address core policies used by DNA Genotek to maintain compliance and assure the proper protections of infrastructure used to store, process, and transmit ePHI for DNA Genotek Customers.

DNA Genotek provides secure and compliant cloud-based software. PaaS Customers utilize hosted software and infrastructure from DNA Genotek to deploy, host, and scale custom developed applications and configured databases. These customers are deployed into compliant containers run on systems secured and managed by DNA Genotek. DNA Genotek does not have insight or access into application level data of PaaS Customers and, as such, does not have the ability to secure or manage risk associated with application level vulnerabilities and security weaknesses. DNA Genotek makes every effort to reduce the risk of unauthorized disclosure, access, and/or breach of PaaS Customer data through network (firewalls, dedicated IP spaces, etc) and server settings (encryption at rest and in transit, OSSEC throughout the Platform, etc).

PaaS Customers can opt for a list of Services from DNA Genotek, which include Backup Service, Logging Service, IDS Service, and Disaster Recovery Service. These services are not standard and PaaS Customers must sign up for them in order for DNA Genotek to manage these areas of security and compliance.

## Compliance Inheritance

***TODO***

DNA Genotek provides compliant hosted software infrastructure for its Customers. DNA Genotek has been through a HIPAA compliance audit by a national, 3rd party compliance firm, to validate and map organizational policies and technical settings to HIPAA rules. DNA Genotek, as a company, and its technology, is HITRUST Certified.  DNA Genotek's infrastructure at Rackspace is HITRUST Certified and certification for AWS, Azure, and SoftLayer are in progress.

DNA Genotek signs business associate agreements (BAAs) with its Customers. These BAAs outline DNA Genotek obligations and Customer obligations, as well as liability in the case of a breach. In providing infrastructure and managing security configurations that are a part of the technology requirements that exist in HIPAA and HITRUST, as well as future compliance frameworks, DNA Genotek manages various aspects of compliance for Customers. The aspects of compliance that DNA Genotek manages for Customers are inherited by Customers, and DNA Genotek assumes the risk associated with those aspects of compliance. In doing so, DNA Genotek helps Customers achieve and maintain compliance, as well as mitigates Customers risk.

Certain aspects of compliance cannot be inherited. Because of this, DNA Genotek Customers, in order to achieve full compliance or HITRUST Certification, must implement certain organizational policies. These policies and aspects of compliance fall outside of the services and obligations of DNA Genotek.

Below are mappings of HIPAA Rules to DNA Genotek controls and a mapping of what Rules are inherited by Customers, both Platform Customers and Add-on Customers.

***END TODO***

## DNA Genotek Organizational Concepts

The physical infrastructure environment is hosted at [Hivelocity](https://hivelocity.net) and [Amazon Web Services](https://aws.amazon.com/) (AWS). The network components and supporting network infrastructure are contained within the Hivelocity and AWS infrastructures and managed by Hivelocity and AWS (respectively). DNA Genotek does not have physical access into the network components. The DNA Genotek environment consists of Juniper firewalls; nginx web servers; Python application servers; PostgreSQL database servers; Logstash logging servers; Linux Ubuntu monitoring servers; Ansible configuration management services; OSSEC IDS services; Docker containers; and developer tool servers running on Linux Ubuntu.

Within the DNA Genotek Platform on Hivelocity and AWS, all data transmission is encrypted and all hard drives are encrypted so data at rest is also encrypted; this applies to all servers - those hosting Docker containers, databases, APIs, log servers, etc. DNA Genotek assumes all data *may* contain ePHI, even though our Risk Assessment does not indicate this is the case, and provides appropriate protections based on that assumption.

It is the responsibility of the Customer to restrict, secure, and assure the privacy of all ePHI data outside of the Application, as this is not under the control or purview of DNA Genotek.

The data and network segmentation mechanism differs depending on the primitives offered by the underlying cloud provider infrastructure:

***TODO***
* Within Hivelocity, Juniper firewalls route traffic to private subnets for SaaS Customers
* Within AWS, hosted load balancers segment data across dedicated Virtual Private Clouds for PaaS Customers and for Platform Add-ons.

The result of segmentation strategies employed by DNA Genotek effectively create RFC 1918, or dedicated, private segmented and separated networks and IP spaces, for each PaaS Customer and for Platform Add-ons.
***END TODO***

Additionally, IPtables is used on each each server for logical segmentation. IPtables is configured to restrict access to only justified ports and protocols. DNA Genotek has implemented strict logical access controls so that only authorized personnel are given access to the internal management servers. The environment is configured so that data is transmitted from the load balancers to the application servers over an SSL encrypted session.

Once the data is received from the application server, a series of Application Programming Interface (API) calls is made to the database servers where the ePHI resides. The ePHI is separated within PostgreSQL databases through programming logic built, so that access to one database server will not present you with the full ePHI spectrum.

The bastion host, nginx web server, and application servers are externally facing and accessible via the Internet. The database servers, where the ePHI resides, are located on the internal DNA Genotek network and can only be accessed directly over an SSH connection through the bastion host. The access to the internal database is restricted to a limited number of personnel and strictly controlled to only those personnel with a business justified reason. Remote access to the internal servers is not accessible except through the load balancers and bastion host.

All SaaS and operating systems are tested end-to-end for usability, security and impact prior to deployment to production.

## Version Control

Policies were last updated February 21, 2017.
