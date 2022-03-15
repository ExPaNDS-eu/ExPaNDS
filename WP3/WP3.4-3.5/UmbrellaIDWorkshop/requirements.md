## UmbrellaID Workshop Preparation

WP3 T3.5 has been discussing the integration of UmbrellaID + Keycloak at the facilities
data catalogues.  
The purpose of this page is to gather the requirements for the workshop and address 
any questions from the participants. 

Please contact wp3@expands.eu if you have any specific requirements or technical questions.

### Confirmed participants
- ALBA, SOLEIL, PSI, HZB, MAXVI, STFC/UKRI, EGI, DESY

### Who will be providing the workshop?
- GEANT: Christos kanellopoulos
- ESRF: Jean Francois Perrin

### Previous workshop provided to PaNOSC
https://indico.psi.ch/event/10773/

### Date of the workshop 
24th March 2022

### Agenda and registration
 https://indico.psi.ch/event/12701/
 

### Requirements

- Integration of Keycloak with UmbrellaID 
- To agree on the sessions that we need 
- How to integrate a service (such us the data catalogue) into keycloak. Small overview (not in detail) To discuss with organisers
-eduTeams intro 

### Checklist for the hands on session 
 
- An installation of keycloak
- Internet access from the host where they have installed keycloak (ideally direct access, but HTTP
  proxy and reverse HTTP proxy are also valid)
- DNS resolution for the host with keycloak installed should be in place and should be identical from   
  everywhere  (I.E. the machine should be referenced with the same domain name from the RI/lab intranet 
  and public internet network)
- A valid X509 server certificate

### Q&A

### Do I need to have Keycloak installed to attend the workshop?
It is not mandatory, however you won't have the full benefit from the hands on session, if you cannot apply it to your own installation right away.

### Does the keycloak instance need to be integrated with internal Active Directory (AD)?

This is not required for the workshop. It is possible to add AD integration later.

You might want to have some sort of integration though, at least before going into production with Keycloak,
because you probably want your AD users to be able to continue to use their credentials to log into Keycloak. 

There are in principle three options to do that:

1. Full integration: Keycloak can use the AD as a storage backend.
   This works at least with an LDAP server.  Not sure if it also works with AD, but I'd guess so.
   But it would mean to store all the Keycloak users in AD and may require Keyclaok to have some sort of
   administrative write access to your AD.  You'd need to discuss with your infrastructure colleagues if
   they'd be happy with that.

2. Partial integration: Keycloak can use the AD as an external identity provider. 
   E.g., users would have two formally independent accounts, one in Keycloak and one in AD,
   but they may link both.
   From that moment on, they will be able to log into Keycloak using AD.
   It requires a little bit of extra scripting (you need a connector that speaks either SAML or OpenID
   Connect to Keycloak and uses AD to authenticate users), but that is not a big deal.  We
   tried that in a test instance and it works.  It's the option that we envision to use at HZB.

3. You may try to implement some sort of external synchronization of the user base between AD and Keycloak.
   I mention that option just for the sake of completeness, I don't believe it would be advisable
   for production.

