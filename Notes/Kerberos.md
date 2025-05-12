NetNTLM - Legacy auth. protocol for compatibility

Assigns users tickets
* Tickets are proof of previous auth.

Flow:
1. User sends their username and a timestamp encrypted using a key made from their password to the **Key Distribution Center** (KDC)
2. KDC create and send back a **Ticket Granting Ticket** (TGT). Along with TGT, a **Session Key** is given, which can generate the following requests
	* TGT is encrypted using **krbtgt** account's password hash
	* Encrypted TGT has a copy of the Session Key in its contents
	* KDC has no need to store the Session Key because it can get it by decrypting the TGT
3. When a user wants to connect to a service on the network, TGT is used to ask the KDC for a **Ticket Granting Service** (TGS). TGS are tickets that allows connection only to the service they were created for. To request a TGS, the user will send their username and timestamp encrypted using the Session Key,