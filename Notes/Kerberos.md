NetNTLM - Legacy auth. protocol for compatibility

Assigns users tickets
* Tickets are proof of previous auth.

Flow:
1. User sends their username and a timestamp encrypted using a key made from their password to the **Key Distribution Center** (KDC)
2. KDC create and send back a **Ticket Granting Ticket** (TGT). Along with TGT, a **Session Key**