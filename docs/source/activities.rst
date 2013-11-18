Activities
==========

Basic Lookup
------------

Example #1 Fetch all the activities in the bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/activities <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/activities>`__

Example #2 Fetch all the activities for an objective
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives/mc3-objective%3A235%40MIT-OEIT/activities <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives/mc3-objective%3A235%40MIT-OEIT/activities>`__

Example #3 Fetch a particular activity by ID
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/activities/mc3-activity%3A222%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/activities/mc3-activity%3A222%40MIT-OEIT>`__

Example #4 Fetch a Particular Activity Without Specifying the Bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar/services/learning/activities/mc3-activity%3A222%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/activities/mc3-activity%3A222%40MIT-OEIT>`__

Example #5 Bulk Fetch Activities by specifying multiple IDs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/activities/bulk?id=activity%3A1%40MIT-OEIT&id=activity%3A2%40MIT-OEIT&id=activity%3A3%40MIT-OEIT <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/activities/bulk?id=activity%3A1%40MIT-OEIT&id=activity%3A2%40MIT-OEIT&id=activity%3A3%40MIT-OEIT>`__

Looking up related objects
--------------------------

Example #1 Fetch a Particular Activity’s Asset IDs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You don’t have to, the asset ids are stored as data fields on the
Activity object!

Example #2 Fetch a Particular Activity’s Assets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/activities/mc3-activity%3A222%40MIT-OEIT/assets <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/activities/mc3-activity%3A222%40MIT-OEIT/assets>`__
