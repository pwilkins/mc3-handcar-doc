Extension Records
=================

What is an extension record?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Extension records allow you to store and retrieve any arbitrary
information you want in a list of name/value pairs.  You may also
optionally store a label used to describe the data field and a
description.  The storage is NOT a key-value pair in that you may store
multiple values against the same name, that way the “field” can
naturally store a list of values.

These name/value pairs are also organized into record types so you may
fetch and update just the group of extension records that you want to
deal with.

FOR NOW you can ignore those types because only one type of extension
record is supported.  Eventually you could optionally specify one or
more record extension types to return just the groups of key value pairs
that you are interested in by adding an optional query param,
“?recordtypeid=xxxxxx”.

==> To update or set the name/value pairs simply get the extension
record, update the bean adding or updating your name value pairs and
then issuing a PUT on the same URL.

See
`ExtensionRecordBean <https://mc3-demo.mit.edu/handcar/contractdocs/ExtensionRecordBean.html>`__\ for
more detailed documentation

Example #1 Fetch a Particular Objective Bank’s Extension Record
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/extension <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/extension>`__

Example #2 Fetch a Particular Objective’s Extension Record
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/extension <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/extension>`__

Example #3 Fetch a Particular Activity’s Extension Record
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/activities/activity%3A1%40MIT-OEIT/extension <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/activities/activity%3A1%40MIT-OEIT/extension>`__

Example #4 Fetch a Particular Asset’s Extension Record
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets/activity%3A444%40MIT-OEIT/extension <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets/activity%3A444%40MIT-OEIT/extension>`__

Example #5 Fetch a Particular Asset Content’s Extension Record
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets/activity%3A444%40MIT-OEIT/assetcontent/activity%3A444%40MIT-OEIT/extension <http://mc3-demo.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A2%40MIT-OEIT/assets/activity%3A444%40MIT-OEIT/assetcontent/activity%3A444%40MIT-OEIT/extension>`__

