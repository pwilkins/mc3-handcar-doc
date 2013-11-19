The Relationship Service
========================

Introduction
------------

Handcar supports an alternative service for accessing and managing
relationships.  These relationships are exposed via the relationship
service.  Key to understand is that they are organized by "families" not
"objective banks" and to map between a bank and a family you need to
call method to get the id of the family that corresponds to the bank you
are working with.  So the pattern is to:

#. Create a bank using the learning service
#. Create objectives via the learning service
#. Switch to the relationship service
#. Use the Bank Id to get the Corresponding Family Id
#. Use that Family Id to get and update the relationships between the
   objectives in the bank

See
`https://mc3-demo.mit.edu/handcar/contractdocs/HandcarRelationshipService.html <https://mc3-demo.mit.edu/handcar/contractdocs/HandcarRelationshipService.html>`__

Objectives have the following known types relationships:

-  Parent-Child (for topic hierarchy)
-  Requisite/Dependent (for pre-requisite mapping)
-  Equivalent
-  Related
-  Corresponds
-  Strongly Corresponds

Each Relationship is an object that contains the following information:

#. Id
#. Name
#. Description
#. Genus Type
#. Source id
#. Destination id

See
`https://mc3-demo.mit.edu/handcar/contractdocs/RelationshipBean.html <https://mc3-demo.mit.edu/handcar/contractdocs/RelationshipBean.html>`__

If I can do pretty much everything I need via the learning service, why would I use the relationship service?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are several reasons you might want to use the relationship service
instead of the learning service:

#. Efficiency Reason #1 -- with the relationship service you can get ALL
   of the relationships of a particular type at the same time.   The
   implementation is faster as well.  Via the learning service you have
   to point to one objective and ask for it’s children traversing the
   hierarchy.  Yes there are bulk operations that can speed things up
   but you still have to traverse the hierarchy tree.
#. Efficiency Reason #2 -- with the relationship service you can get ALL
   of the relationships for ALL types of relations at the same time.
    Most banks are not that large and if you are painting a screen with
   the objects and relationships the relationship service can get all
   that data in one call and very quickly.
#. Extra Data -- with the relationship service you can tag the
   relationship with extra data such as name or description or other
   extension data.  This allows you to display more detailed labels
   describing your relationships.  With learning service the names and
   descriptions are based on the type of the relationship.

If I can do pretty much everything I need via the relationship service, why would I use the learning service?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are several reasons why you might want to manage the relationships
via the learning service:

#. Efficiency #1 -- If you are painting the hierarchy tree one node at a
   time the learning service more naturally supports those kinds of
   operations.  You use that to get just the nodes you want to paint
   WITHOUT GETTING ALL of the relationships.
#. Efficiency #2 -- Most of the time the essence of a relationship is
   just that the the two ids on either end of the relationship.  The
   learning service exposes just the critical information that is really
   needed to manage most relationships.  I.e. you don’t have to specify
   all that “extra data.”
#. Ordering -- with the learning service, when you can add multiple
   children to an objective the ordering of those children is guaranteed
   to be preserved.  That is when you fetch back the children they will
   be retrieved in the same order.  With the relationship service you
   can only create one relationship at a time with no way to specify
   ordering of multiple relationships.

Can I use both in the same application?  (Do the two services really update the same data?)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes! Welcome to service oriented architecture.  Underneath, both
services talk to the same database tables.  If for example you add 2
child objectives to another objective you can immediately turn around
and fetch those as a PARENT-CHILD relationship.   Conversely if you add
a REQUISITE relationship via the relationship service you can then ask
via the learning service which objectives does this one depend on and it
will return you the same result.  The beauty is that you can use
whichever form best supports your particular application.

Basic Lookup
------------

Example #1 Getting the Family Id for the corresponding Objective Bank Id and vice versa
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar/services/relationship/familyidforbank/mc3-objectivebank%3A1%40MIT-OEIT <https://mc3-demo.mit.edu/handcar/services/relationship/familyidforbank/mc3-objectivebank%3A1%40MIT-OEIT>`__

and vice versa (in case you need to go back)

`https://mc3-demo.mit.edu/handcar/services/relationship/bankidforfamily/mc3-family%3A1%40MIT-OEIT <https://mc3-demo.mit.edu/handcar/services/relationship/bankidforfamily/mc3-family%3A1%40MIT-OEIT>`__

Example #2 Get a list of all the families of relationships
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar/services/relationship/families <https://mc3-demo.mit.edu/handcar/services/relationship/families>`__

Example #3 Get a single family by Id
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar/services/relationship/families/mc3-family%3A1%40MIT-OEIT <https://mc3-demo.mit.edu/handcar/services/relationship/families/mc3-family%3A1%40MIT-OEIT>`__

Example #4 Get a list of all of all relationships in a family, optionally by relationship type
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar/services/relationship/families/mc3-family%3A1%40MIT-OEIT/relationships <https://mc3-demo.mit.edu/handcar/services/relationship/families/mc3-family%3A1%40MIT-OEIT/relationships>`__

To specify the type or types just add the query parameter for that type

`https://mc3-demo.mit.edu/handcar/services/relationship/families/mc3-family%3A1%40MIT-OEIT/relationships?genustypeid=mc3-relationship%3Amc3.lo.2.lo.requisite%40MIT-OEIT <https://mc3-demo.mit.edu/handcar/services/relationship/families/mc3-family%3A1%40MIT-OEIT/relationships?genustypeid=mc3-relationship%3Amc3.lo.2.lo.requisite%40MIT-OEIT>`__

Example #5 Get a particular relationship
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar/services/relationship/families/mc3-family%3A1%40MIT-OEIT/relationships/mc3-relationship%3A1%40MIT-OEIT <https://mc3-demo.mit.edu/handcar/services/relationship/families/mc3-family%3A1%40MIT-OEIT/relationships/mc3-relationship%3A1%40MIT-OEIT>`__

