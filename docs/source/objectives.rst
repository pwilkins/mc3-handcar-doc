Objectives
==========

Objectives come in two types: TOPICs and OUTCOMEs.

Basic Lookups
-------------

Example #1 Finding all TOPIC objectives within a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives?genustypeid=mc3-objective%3Amc3.learning.topic%40MIT-OEIT <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives?genustypeid=mc3-objective%3Amc3.learning.topic%40MIT-OEIT>`__

Example #2 Finding all OUTCOME objectives within a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives?genustypeid=mc3-objective%3Amc3.learning.outcome%40MIT-OEIT <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives?genustypeid=mc3-objective%3Amc3.learning.outcome%40MIT-OEIT>`__

Example #3 Finding an objective by id within a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT>`__

Example #4 Finding an objective by id without knowing it’s bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can also find an objective (given an Id even if you do not know the
objective bank where it is stored.
`http://oki-dev.mit.edu/handcar/services/learning/objectives/objective%3A1%40MIT-OEIT <http://oki-dev.mit.edu/handcar/services/learning/objectives/objective%3A1%40MIT-OEIT>`__

Example #5 Bulk fetching lots of objectives by id
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you have a list of ids for objectives in a bank and you want to fetch
them all at once you can do this by specifying BULK in the url then
listing the ids as query parameters.

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/bulk?id=objective%3A1%40MIT-OEIT&id=objective%3A14%40MIT-OEIT&id=objective%3A27%40MIT-OEIT <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/bulk?id=objective%3A1%40MIT-OEIT&id=objective%3A14%40MIT-OEIT&id=objective%3A27%40MIT-OEIT>`__

Looking up objectives in a hierarchy
------------------------------------

Topics are often nested or organized into a hierarchy so that they have
parents and children so that topics may have sub-topics and
sub-sub-topics finally ending in specific outcomes.  Note: Although the
typical pattern is that topics have parent child relationships, the
system also supports the creations of outcomes that themselves have
child children.

Example #1 Finding the root objectives or just the root ids in the hierarchy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/roots <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/roots>`__

This returns the root objectives AND it’s children down to a depth of 10
levels deep.  This is called an “ObjectiveNode” because contains all the
fields of an objective but also contains three extra fields:

-  isRoot -- indicates if this is an absolute root in the underlying
   representation
-  isLeaf -- indicates if this is an absolute leaf in the underlying
   representation
-  List of the objective’s children but with these

You can optionally add a query parameter “descendentlevels” to restrict
or expand the levels down it goes down.  For example this gets just the
root objectives with no children.

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/objectives/roots?descendentlevels=0 <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/objectives/roots?descendentlevels=0>`__

You can also just get the ids of the root objectives

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/rootids <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/rootids>`__

Example #2 Finding an objective’s children or just the ids of it’s children
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/children <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/children>`__

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/childids <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/childids>`__

Example #3 Finding an objective’s parent(s) or just the ids of it’s parent(s)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A2%40MIT-OEIT/parents <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A2%40MIT-OEIT/parents>`__

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A2%40MIT-OEIT/parentids <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A2%40MIT-OEIT/parentids>`__

Note: most objectives have just ONE parent but the system allows for a
topic to fall under multiple parents, for example ROBOTICS might have
both COMPUTER SCIENCE and MECHANICAL ENGINEERING as parents.

Example #4 Bulk fetching of an objective’s children, grandchildren, great-grandchildren, etc 10 levels deep
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/children/bulk <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/children/bulk>`__

You may also optionally specify the depth of the hierarchy to return by
supplying a query parameter  “?descendentlevels={n}” so that this
returns just the objective with no children.

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/children/bulk?descendentlevels=0 <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/children/bulk?descendentlevels=0>`__

Looking up requisite and dependent objectives
---------------------------------------------

Objectives can also be organized into chains of pre-REQUISITES.  These
are objectives that typically must be mastered before attempting to
master the current objective.

Example #1 Finding the beginner objectives or just the beginner ids for the bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

These are just the objectives in the bank that do not have any REQUISITE
objectives defined.

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/beginners <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/beginners>`__

This gets the beginner objectives down to 10 levels deep to restrict or
increase the levels you can add an optional query parameter
“descendentlevels”

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/beginners?descendentlevels=0 <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/beginners?descendentlevels=0>`__

You can also just get the begnner ids.

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/beginnerids <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/beginnerids>`__

Example #2 Finding an objective’s immediately preceding requisite objectives
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For example: Anti-derivative has three requisites: Function, Derivative,
and Differential

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/requisites <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/requisites>`__

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/requisiteids <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/requisiteids>`__

Example #3 Finding the objectives that are immediately dependent on a particular objective
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A134%40MIT-OEIT/dependents <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A134%40MIT-OEIT/dependents>`__

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A134%40MIT-OEIT/dependentids <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A134%40MIT-OEIT/dependentids>`__

Example #4 Bulk fetching of an objective’s dependents, that dependent’s dependent’s, etc 10 levels deep
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/dependents/bulk <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/dependents/bulk>`__

Note: it returns that single objective but also with three extra fields:

-  isRoot -- indicates if this is an absolute root in the underlying
   representation
-  isLeaf -- indicates if this is an absolute leaf in the underlying
   representation
-  List of the objective’s children but with these

You may also optionally specify the depth of the hierarchy to return by
supplying a query parameter “?descendentlevels={n}” like this so that
this returns just the objective with no dependents.

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/dependents/bulk?descendentlevels=0 <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/dependents/bulk?descendentlevels=0>`__
