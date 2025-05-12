NetNTLM - Legacy auth. protocol for compatibility

Assigns users tickets
* Tickets are proof of previous auth.

Flow:
1. User sends their username and a timestamp encrypted using a key made from their password to the **Key Distribution Center** (KDC)
2. KDC create and send back a **Ticket Granting Ticket** (TGT). Along with TGT, a **Session Key** is given, which can generate the following requests
	* TGT is encrypted using **krbtgt** account's password hash
	* Encrypted TGT has a copy of the Session Key in its contents
	* KDC has no need to store the Session Key because it can get it by decrypting the TGT
3. When a user wants to connect to a service on the network, TGT is used to ask the KDC for a **Ticket Granting Service** (TGS). TGS are tickets that allows connection only to the service they were created for. To request a TGS, the user will send their username and timestamp encrypted using the Session Key, and also the TGT and **Service Principal Name** (SPN). 
4. KDC will send a TGS with a **Service Session Key**, which is needed to authenticate to the service. TGS is encrypted using a key derived from **Service Owner Hash**. The Service Owner is the user or machine account that the service runs under. TGS contains a copy of the Service Session Key, can be recovered by Service Owner through decryption.
5. TGS sent to service to authenticate and establish a connection. Service uses configured 

![](images/thm-kerb-tgt.png)

![](images/thm-kerb-tgs.png)

![](images/thm-kerb-auth.png)