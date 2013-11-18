Administration -- Deleting objects
==================================

Delete Objective Bank
---------------------

Example #1 Delete an Objective Bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

DELETE
`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT>`__

TODO: create an example in cURL or HURLit

What happens when I delete an objective bank?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Most people cannot delete an objective bank -- such authority is
   restricted to just those who have the “DELETE LO BANK” role, a
   tightly controlled group.
#. If you do have rights, the attempt fails if any objectives exist in
   the Bank -- you must delete them first
#. Any assets you may have created in the corresponding repository are
   not deleted

#. Leaves a Repository in existence that “corresponds” to the bank in
   question but at present there is no way to access any of those assets
   via handcar

4. Any relationships should have already been deleted since all
   objectives must have been deleted already

2. Leaves a family floating around that “corresponds” to the bank in
   question that can be viewed via the Relationship Service but should
   probably be left alone.

Delete Objective
----------------

Example #1 Delete an Objective
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

DELETE
`https://oki-dev.mit.edu/handcar/services/learning/objectives/ <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT>`__

TODO: create an example in cURL or HURLit

What happens when I delete an objective?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Fails if any activities exist -- you must delete them first
#. Does not check if there are any related assets in the corresponding
   repository so those assets do not get deleted when the activity that
   points to them gets deleted.
#. Does check for and deletes any relationships TO or FROM the objective
   that is being deleted

#. BUG: If the relationship crosses banks (i.e. points FROM an objective
   in a different bank TO the objective being deleted then the
   relationship does not get deleted -- this is a known bug and will be
   addressed when we implement more cross-bank support.

Delete Activity
---------------

Example #1 Delete an Activity
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

DELETE
`https://oki-dev.mit.edu/handcar/services/learning/activities <https://oki-dev.mit.edu/handcar/services/learning/activities>`__

TODO: create an example in cURL or HURLit

What happens when I delete an activity?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. It’s links to it’s assets are automatically removed but the assets
   themselves are not deleted

Delete Asset
------------

Note: Our repository implementation does not actually store the contents
of an asset, just a URL where it can be found on the internet.  So when
we say “delete an asset” we really mean deleting the metadata about the
asset.  This metadata  is stored in an OSID object.  We are not talking
about deleting the actual movie or photo or website itself.

Example #1 Delete an Asset
~~~~~~~~~~~~~~~~~~~~~~~~~~

DELETE
`https://oki-dev.mit.edu/handcar/services/learning/assets/ <https://oki-dev.mit.edu/handcar/services/learning/activities>`__

TODO: create an example in cURL or HURLit

What happens when I delete an asset?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Since the asset contents are embedded in the asset object they are
   are automatically deleted along with the asset
#. Activities that point to these assets have their link to that asset
   removed.

Delete Asset Content
--------------------

Example #1 Delete an Asset Content
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note: Our repository implementation does not actually store the contents
of an asset, just a URL where it can be found on the internet.  So when
we say “delete an asset content” we really mean deleting the metadata
about the content of that asset.  This metadata  is stored in an OSID
object.  We are not talking about deleting the actual movie or photo or
website itself.

You delete an asset content by simply removing it from inside of the
asset and updating the asset

PUT
`https://oki-dev.mit.edu/handcar/services/learning/assets/ <https://oki-dev.mit.edu/handcar/services/learning/activities>`__

TODO: create an example in cURL or HURLit

What happens when I delete an asset content?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. Since the asset contents are do not actually contain the physical
   asset but just the URL so just the contents are deleted.

Delete a Relationship Family
----------------------------

Remember each objective bank has a corresponding “family” that holds the
relationships for that bank so you don’t really want to delete a family.
 In fact, you cannot directly delete a family via handcar.

Delete a Relationship
---------------------

Example #1 Delete a Relationship

DELETE
`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT>`__

TODO: create an example in cURL or HURLit

What happens when I delete a Relationship?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. The corresponding relationship when viewed from the learning service
   disappears as well.  For example if you delete a parent-child
   relationship via the relationship service the parent-child
   relationship is gone if you turn around and ask for the children of
   the objective via the learning service.
