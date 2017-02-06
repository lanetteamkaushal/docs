# What's new in Version 3?

We've made some big changes to Gluu Sever 3.0 to make it more modern, 
faster, and easier to manage. The following is an overview of changes.

## Jetty replaces Tomcat as servlet container

Here are some of the reasons we made this change:

 - Memory management: easier to allocate memory per app.
 - Restart: Easier to restart individual components without affecting
   others. For example, Asimba requires more restarts when certain
   configuration is updated.
 - Logs: `wrapper.log` was getting too busy. It's better to have
   the top-level log smaller. See [logs management](./logs.md) 
   for more informatoin.
 - Network: oxAuth is Internet facing; oxTrust is an admin application
   which may be internal facing only.
 - Docker: Deploying each application in it's own servlet container 
   aligns with our strategy to deploy each application in its own 
   container.

## OpenLDAP replaces OpenDJ

The Gluu Server uses LDAP for persistence. The Gluu Server will continue to support 
several LDAP servers (including OpenDJ), but will now ship with OpenLDAP. Below are a few
reasons.

 - OpenLDAP has a better license, and [Symas](https://symas.com/) (the company behind OpenLDAP),
   has a clear commitment to free open source software.
 - OpenLDAP's LMDB backend is super fast and crash-resistant. 
 - Tired of fighting with Java garbage collection.
 - [Affordable support options](https://symas.com/services/subscriptions/) from Symas.
 - Proxy Capabilities: using OpenLDAP Gold, which is a commercial 
   distribution from Symas, data can be organized into different replicated 
   topologies, and the proxy can be used to route operations. This strategy
   can increase the write performance of the LDAP service. 

## Shibboleth IDP version 3

 - Re-architected to use Spring
 - Version 2.0 was end of life
 - For more information, see the [Release Notes](https://wiki.shibboleth.net/confluence/display/IDP30/ReleaseNotes)

## New Features

 - Passport.js makes it easy to offer your users social login at more than 300 websites and consumer IDPs. See the [Passport](../authn-guide/passport.md) docs for more information.
 - One-Time Password (OTP) authentication: You asked for it! Now it's easy to authenticate users with any standard HOTP or TOTP OATH 
   software, like [Google Authenticator](https://support.google.com/accounts/answer/1066447?hl=en).
 - Centralized logging--useful for clustered deployments.
 - Improved audit logging capabilities for OAuth 2.0
