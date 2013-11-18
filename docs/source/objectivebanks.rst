===============
Objective Banks
===============

All data is organized into collections called objective banks.  Right
now we have several such banks, for example: Crosslinks, ChemBridge, and
i2.002 and EDC.  These are projects where MIT professors mapped the
concepts of their respective domains.  MC3 is a federated system so we
can add in objectives from other sources easily.  Later we will be
adding additional banks from within and outside of MIT.

Basic Lookup
------------

Example #1 Get a list of all objective banks
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks>`__ 

Example on\ ` Hurl
It <http://www.hurl.it/hurls/e90060389942ccd3cddd50045a0a7925065dd297/7945e28ff26be22b0a12d6ce0a20698aa3c56343>`__

Example #2 Get the details of a particular objective bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT>`__ 

Looking up objects within a bank
--------------------------------

Example #1 Finding all objectives within a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives>`__

Example #2 Finding all activities within a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/activities <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/activities>`__

Example #3 Finding all assets tied to a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/assets <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/assets>`__

Configuration Data
------------------

Each bank is designed to be configured to support different
categorization schemes and types.

As mentioned above objectives come in two basic varieties or genus
types: TOPIC and OUTCOMES and the default categorization scheme uses
Bloom’s taxonomy.

Example #1 Finding all the allowed objective types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/types/genus/objective <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/types/genus/objective>`__

Should return three types, one for TOPIC, one for OUTCOMEs and one for a
special type called “GENERIC OUTCOME”

Technically the types for objectives, activities and assets can all be
configured per bank.  In practice, all of our current banks use the same
set of types for these kinds of objects.

Example #2 Finding the scaling systems (Bloom’s Taxonomy) used to categorize the objectives
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note: in the literature this is called the “Cognitive Process” scale and
the “Knowledge Category” scale.  see this
`handout <http://www.google.com/url?q=http%3A%2F%2Fwww.celt.iastate.edu%2Fpdfs-docs%2Fteaching%2FRevisedBloomsHandout.pdf&sa=D&sntz=1&usg=AFQjCNHdUp-E85rfxZQ1bm-1ItkOiwXGKg>`__ 
from Iowa State University.  See
`https://oki-dev.mit.edu/handcar-authn/contractdocs/GradeSystemBean.html <https://oki-dev.mit.edu/handcar-authn/contractdocs/GradeSystemBean.html>`__

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/gradesystems/cognitiveprocess <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/gradesystems/cognitiveprocess>`__

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/gradesystems/knowledgecategory <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/gradesystems/knowledgecategory>`__

Example #3 Getting a description of the grades used in the bloom types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This gets all the grades

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/grades <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/grades>`__

This gets information on a particular grade

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/grades/mc3.grade.system.cognitive.process.crosslinks%3Amc3.grade.bloom.learn%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/grades/mc3.grade.system.cognitive.process.crosslinks%3Amc3.grade.bloom.learn%40MIT-OEIT>`__

Right now this is the only configuration that varies by objective bank.
 Crosslinks banks just have LEARN and APPLY. The EDC bank has no grades
in it’s scale and the rest have the full Bloom taxonomy.

DoI I have to use Bloom’s Taxonomy?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No you do not have to use Bloom’s taxonomy.  Bloom categorization of
objectives is completely optional.

If you want to use a different taxonomy that can be accommodated as
well.  If we create an objective bank for you we can also configure it
with any taxonomy you want.  It can be a subset of Bloom’s, an
alternative to Bloom’s or it can be configured to allow no taxonomy at
all.  Some caveats:

-  We must do the configuration for you -- we do not yet support
   configuration of the bank via the REST interface
-  Some of MC3’s tools are wired to work only with Bloom’s taxonomy and
   may not work as expected if you do not use Bloom’s.

Final note:

-  If you just don’t like the default labeling we used for Bloom then we
   can configure your bank to use Bloom’s keys use your own labeling

-  For example: you may wish to use the word “Knowledge” instead of
   “Remember” to describe the bloom type but underneath they still point
   to the same Bloom category.

Example #4 Finding all the activity types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/activity <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/activity>`__

Note: Right now there is three broad types of activities supported ASSET
BASED, ASSESSMENT BASED and COURSE BASED but the only one currently in
use is the ASSET BASED.

Example #5 Finding all the asset types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/assets <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/assets>`__

Note: Right now there is only one asset type is supported it is an asset
that points to a URL.

Example #6 Finding all the asset content (mime) types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/assetcontent <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/assetcontent>`__

Note: There is a special type for UNKNOWN  FORMAT TYPE.  that you can
use if you don’t know the mime type of the asset.

Note: the list returned right now is NOT complete.  It just contains
TEXT based format types, we will very soon be adding in types, like MPG
for movings and JPG for sound.

Example #7 Get a list of all known types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar-authn/services/learning/types/ <https://oki-dev.mit.edu/handcar-authn/services/learning/types/>`__

Example #8 Get a list of objective bank types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/types/genus <https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/types/genus>`__

Example #9 Get a list of Display Text Language Types (and default)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/languages <https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/languages>`__

Get the default (english for all the current banks)

`https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/languages/default <https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/languages/default>`__

Example #10 Get a list of Display Text Script Types (and default)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/scripts <https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/scripts>`__

Get the default (latin for all the current banks)

`https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/scripts/default <https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/scripts/default>`__

Example #11 Get a list of Display Text Format Types (and default)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/formats <https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/formats>`__

Get the default (latin for all the current banks)

`https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/formats/default <https://oki-dev.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/formats/default>`__

