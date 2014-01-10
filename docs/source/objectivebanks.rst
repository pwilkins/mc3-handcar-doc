===============
Objective Banks
===============

All data is organized into collections called objective banks.  Right
now we have several such banks, for example: Crosslinks, ChemBridge, 
i2.002 and EDC.  These are projects where MIT professors mapped the
concepts of their respective domains.  MC3 is a federated system so we
can add objectives from other sources easily.  Later we will 
add additional banks from within and outside of MIT.

Basic Lookup
------------

Example #1 Get a list of all objective banks
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks>`__ 

Example on\ ` Hurl
It <http://www.hurl.it/hurls/e90060389942ccd3cddd50045a0a7925065dd297/7945e28ff26be22b0a12d6ce0a20698aa3c56343>`__

Example #2 Get the details of a particular objective bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT>`__ 

Looking up objects within a bank
--------------------------------

Example #1 Find all objectives within a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives>`__

Example #2 Find all activities within a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/activities <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/activities>`__

Example #3 Find all assets tied to a bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/assets <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/assets>`__

Configuration Data
------------------

Each bank is designed to be configured to support different
categorization schemes and types.

As mentioned above objectives come in three basic varieties or genus
types: TOPIC, OUTCOME, and GENERIC_OUTCOME, and the default categorization scheme uses
Bloom’s taxonomy.

Example #1 Find all the allowed objective types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/types/genus/objective <https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/types/genus/objective>`__

Should return three types, one for TOPIC, one for OUTCOMEs and one for a
special type called “GENERIC OUTCOME”

Technically the types for objectives, activities and assets can all be
configured by bank.  In practice, all of our current banks use the same
set of types for these kinds of objects.

Example #2 Find the scaling systems (Bloom’s Taxonomy) used to categorize the objectives
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note: in the literature this is called the “Cognitive Process” scale and
the “Knowledge Category” scale.  see this 
`PDF Handout <http://www.celt.iastate.edu/pdfs-docs/teaching/RevisedBloomsHandout.pdf>`__ 
from Iowa State University.  See
`https://mc3-demo.mit.edu/handcar-authn/contractdocs/GradeSystemBean.html <https://mc3-demo.mit.edu/handcar-authn/contractdocs/GradeSystemBean.html>`__

`https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/gradesystems/cognitiveprocess <https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/gradesystems/cognitiveprocess>`__

`https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/gradesystems/knowledgecategory <https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/gradesystems/knowledgecategory>`__

Example #3 Get a description of the grades used in the bloom types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This gets all the grades

`https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/grades <https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/grades>`__

This gets information on a particular grade

`https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/grades/mc3.grade.system.cognitive.process.crosslinks%3Amc3.grade.bloom.learn%40MIT-OEIT <https://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/grades/mc3.grade.system.cognitive.process.crosslinks%3Amc3.grade.bloom.learn%40MIT-OEIT>`__

Right now this is the only configuration that varies by objective bank.
 Crosslinks banks just have LEARN and APPLY. The EDC bank has no grades
in its scale and the rest have the full Bloom taxonomy.

DoI I have to use Bloom’s Taxonomy?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No you do not have to use Bloom’s taxonomy.  Bloom categorization of
objectives is completely optional.

We can accomodate other taxonomies as 
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
   can configure your bank to use Bloom’s keys or use your own labeling.

-  For example: you may wish to use the word “Knowledge” instead of
   “Remember” to describe the bloom type but underneath they still point
   to the same Bloom category.

Example #4 Find all the activity types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/activity <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/activity>`__

Note: Right now there is three broad types of activities supported ASSET
BASED, ASSESSMENT BASED and COURSE BASED but the only one currently in
use is the ASSET BASED.

Example #5 Find all the asset types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/assets <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/assets>`__

Note: Right now there is only one asset type is supported it is an asset
that points to a URL.

Example #6 Find all the asset content (mime) types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/assetcontent <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/types/genus/assetcontent>`__

Note: There is a special type for UNKNOWN  FORMAT TYPE.  that you can
use if you don’t know the mime type of the asset.

Note: the list returned right now is NOT complete.  It just contains
TEXT based format types, we will very soon be adding in types, like MPG
for movings and JPG for sound.

Example #7 Get a list of all known types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar-authn/services/learning/types/ <https://mc3-demo.mit.edu/handcar-authn/services/learning/types/>`__

Example #8 Get a list of objective bank types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/types/genus <https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/types/genus>`__

Example #9 Get a list of Display Text Language Types (and default)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/languages <https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/languages>`__

Get the default (english for all the current banks)

`https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/languages/default <https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/languages/default>`__

Example #10 Get a list of Display Text Script Types (and default)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/scripts <https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/scripts>`__

Get the default (latin for all the current banks)

`https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/scripts/default <https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/scripts/default>`__

Example #11 Get a list of Display Text Format Types (and default)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/formats <https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/formats>`__

Get the default (latin for all the current banks)

`https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/formats/default <https://mc3-demo.mit.edu/handcar-authn/services/learning/objectivebanks/mc3-objectivebank%3A2%40MIT-OEIT/types/formats/default>`__

