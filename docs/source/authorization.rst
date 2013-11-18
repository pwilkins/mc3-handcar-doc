Authorization
=============

The MC3$GUEST account
---------------------

Unauthenticated access requires no keys but there are limits on what you
can do.  You may:

#. View objectives in most but not all banks

#. Some faculty wish to keep their banks private
#. right now the only banks like that are the Course 16 ABET
   accreditation bank.

2. Create, update and delete “sandbox banks”

3. These are “play areas” that are periodically destroyed on the
   non-production tiers (MC3-DEMO)

#. See database refresh cycle

4. You do not “own” a sandbox just because you created it

2. Anyone can view, update, change or delete data in your sandbox.

MIT Roles
---------

All authorizations are stored and managed via the\ ` MIT Roles database
system <http://web.mit.edu/rolesdb/>`__.  This system is accessed
dynamically in real-time to assess if a user is or is not authorized to
access a resource.

Roles are managed via the MIT Roles Web pages by authorized users.  It’s
roles category is MC3.

The possible authorizations are:

` <#>`__\ ` <#>`__

Role

Description

Notes

DELETE LO BANK

Allows a user to delete an entire objective bank and everything in it

Tightly restricted

READ LO DATA

Allows the user to read and view all of the Objective data in the bank

READ ACTIVITY DATA

Allows the user to read and view activities in the bank

READ RELATIONSHIP DATA

Allows the user to read and view relationships between objectives

READ ASSET REFERENCE DATA

Allows the user to read and view the meta data about an external asset.

MC3 does not store assets it just stores data about the asset and the
URL by which it can be accessed.

MAINTAIN LO DATA

Allows the user to create, update and delete objectives

MAINTAIN ACTIVITY DATA

Allows the user to create, update and delete activity data

MAINTAIN RELATIONSHIP DATA

Allows the user to create

MAINTAIN ASSET REFERENCE DATA

Allows the user to create a new asset reference, and update or delete
this the metadata about an external asset

Qualifiers
----------

User authorizations can also be assigned “qualifiers.” These qualifiers
map to objective banks that exist in handcar.

==> Right now the mapping is via the GENUS TYPE of the objective bank
but that may change in the future.

What if a user has no authorizations?
-------------------------------------

By definition all users have AT LEAST as much rights as the MC3$GUEST
user.  So if a user doesn’t have the authorization but MC3$GUEST does
then then the user can access that resource.

Authorization Hints
-------------------

Handcar provides you with “hints” to allow you to write an application
that responds gracefully to authorization blocks.  For example if a
person does not have the rights to create an objective then the
application can check these hints to disable the “create” button.

These are designed to be just "hints" and not be definitive
authorization checks.  Actual authorization checks could be much more
fine grained.  So... although we are not doing this right now, it is
possible that a person may have general access to update objectives in a
bank but not be able to update this objective because it is “special”
say a root objective that only certain people can update.

Also, a false hint value could mean that the underlying service simply
does not support that operation. Although we are not doing this right
now we plan on integrating with other read-only banks.  In this
situation it would be false because NO ONE can update it's objectives
because it is read-only.

This is the contractdocs for the authorization hints:

`https://oki-dev.mit.edu/handcar/contractdocs/AuthorizationHintsBean.html <https://oki-dev.mit.edu/handcar/contractdocs/AuthorizationHintsBean.html>`__

Example #1 getting authorization hints for MC3GUE$T for the Chembridge bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This shows that GUEST can read Chembridge data but not update it.

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/authorization <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/authorization>`__

Example #2 getting your own authorization hints for the Chembridge bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note that since this URL requires authorization it shows you your own
personal access to chembridge

`https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank:2@MIT-OEIT/authorization <https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank:2@MIT-OEIT/authorization>`__

