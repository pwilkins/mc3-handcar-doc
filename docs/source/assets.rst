Assets
======

Basic Lookup
------------

Example #1 Fetch all Assets associated with an objective bank optionally restricted by Genus type(s)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets>`__

or

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets?genusTypeId=mc3-asset%3Amc3.learning.asset.url%40MIT-OEI <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets?genusTypeId=mc3-asset%3Amc3.learning.asset.url%40MIT-OEIT>`__

you can also bulk fetch assets using multiple Genus types by adding
“&genustypeid={genusTypeId2}” etc.

Example #2 Fetch a particular asset from a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets/activity%3A251%40MIT-OEIT <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets/activity%3A251%40MIT-OEIT>`__

Example #3 Fetch a particular asset without Specifying Bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/assets/activity%3A251%40MIT-OEIT <http://mc3-demo.mit.edu/handcar/services/learning/assets/activity%3A251%40MIT-OEIT>`__

Example #4 Bulk Fetch Multiple Particular Assets Within an Objective Bank by ID
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank:1@MIT-OEIT/assets/bulk?id=mc3-asset%3A38%40MIT-OEIT&id=mc3-asset%3A39%40MIT-OEIT&id=mc3-asset%3A40%40MIT-OEIT&id=mc3-asset%3A41%40MIT-OEIT <https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank:1@MIT-OEIT/assets/bulk?id=mc3-asset%3A38%40MIT-OEIT&id=mc3-asset%3A39%40MIT-OEIT&id=mc3-asset%3A40%40MIT-OEIT&id=mc3-asset%3A41%40MIT-OEIT>`__

Example #5 Fetch a Particular Objective Asset’s Branding Information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Branding information is not supported yet.
