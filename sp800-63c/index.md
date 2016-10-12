---
layout: page
title: "SP 800-63C"
description: "SP 800-63C"
---

# SP 800-63C

This is a working draft of NIST Special Publication 800-63C, *Assertions and Federation*. This document is a sub-document referenced by [SP 800-63-3](../sp800-63-3/) covering the associated topics that had been previously in SP 800-63-2.

SP 800-63C provides guidance on the use of assertions to convey the results of authentication processes to a relying party. Assertions are used in federated identity systems where the authentication is performed by a credential service provider or a verifier (sometimes called an Identity Provider) and used by a different party (sometimes called a Relying Party). Federation permits a centrally-managed set of credentials to be used at a number if different relying parties.

Keys and other secrets used to maintain state (stored in cookies, local storage, etc.) have been previously characterized as local assertions, but have very different requirements and characteristics than assertions conveyed between different parties. Accordingly, such "local assertions" are treated as reauthentication secrets and covered in SP 800-63B.
