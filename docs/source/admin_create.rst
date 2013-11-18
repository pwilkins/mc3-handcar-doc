===========================================================
Administration -- Creating and Updating Objects in Handcar
===========================================================

A Word about Types
------------------

Handcar uses “types” to organize and categorize the various objects it
manages.

==>  ALL OBJECTS MUST BE ASSIGNED A TYPE.

You can query the configuration (see above) to find out which types that
are allowed for your particular objective bank.  However there are ones
that are commonly used across banks.  You should create a “constants”
file to hold these types to make it easier to create objects in the
system.

List of Common “Handy Dandy” Types
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

` <#>`__\ ` <#>`__

Applies to

Name

Value

Objective Banks

Sandbox Bank

mc3-objectivebank%3Amc3.learning.objectivebank.sandbox%40MIT-OEIT

Objectives

Topic

mc3-objective%3Amc3.learning.topic%40MIT-OEIT

Objectives

Outcome

mc3-objective%3Amc3.learning.outcome%40MIT-OEIT

Objectives

Generic Outcome

mc3-objective%3Amc3.learning.generic.outcome%40MIT-OEIT

Activity

Asset Based Activity

mc3-activity%3Amc3.learning.activity.asset.based%40MIT-OEIT

Activity

Generic Activity

mc3-activity%3Amc3.learning.activity.generic%40MIT-OEIT

Asset

URL Based Asset

mc3-asset%3Amc3.learning.asset.url%40MIT-OEIT

Asset Content

(mime type)

Unknown (unspecified)

mc3-asset-content%3Amc3.learning.asset.content.unknown%40MIT-OEIT

Display Text Format

Plain Text

Text+Formats%3Aplain%40okapia.net

Display Text Format

HTML + Latex

Text+Formats%3AHTML%2BLaTeX%40okapia.net

Display Text Language

English

639-2%3AEnglish%40ISO

Display Text Script

Latin

15924%3ALatin%40ISO

Cognitive Process

Analyze

mc3.grade.system.cognitive.processes.bloom.revised%3Amc3.grade.bloom.analyze%40MIT-OEIT

Cognitive Process

Create

mc3.grade.system.cognitive.processes.bloom.revised%3Amc3.grade.bloom.create%40MIT-OEIT

Cognitive Process

Evaluate

mc3.grade.system.cognitive.processes.bloom.revised%3Amc3.grade.bloom.evaluate%40MIT-OEIT

Cognitive Process

Learn

mc3.grade.system.cognitive.processes.bloom.revised%3Amc3.grade.bloom.learn%40MIT-OEIT

Cognitive Process

Remember

mc3.grade.system.cognitive.processes.bloom.revised%3Amc3.grade.bloom.remember%40MIT-OEIT

Knowledge Category

Factual

mc3.grade.system.knowlege.categories.bloom.revised%3Amc3.grade.factual%40MIT-OEIT

Knowledge Category

Procedural

mc3.grade.system.knowlege.categories.bloom.revised%3Amc3.grade.procedural%40MIT-OEIT

Knowledge Category

Meta-cognitive

mc3.grade.system.knowlege.categories.bloom.revised%3Amc3.grade.metacognitive%40MIT-OEIT

Knowledge Category

Conceptual

mc3.grade.system.knowlege.categories.bloom.revised%3Amc3.grade.conceptual%40MIT-OEIT

How can I get my own objective bank in the production tier on MC3?
------------------------------------------------------------------

MC3 was designed to support MIT faculty and their academic interests.
 If you are a faculty member (or work with one) simply send  us an email
at
`handcar-help@mailman.mit.edu <mailto:handcar-help@mailman.mit.edu>`__ and
we will set one up for you immediately.  If you are not a faculty member
but are part of the larger MIT community then we can probably support
you as well.  If you are not part of the MIT community please contact us
anyway and we may be able to work out some sort of other arrangement.

Creating a “Sandbox” Objective Bank in MC3-DEMO
-----------------------------------------------

Objective Banks cannot be directly created by end users in the
production tier (MC3) but Sandbox banks can be created in the DEMO tier
(MC3-DEMO).

Some cautions

#. If you create a sandbox bank, it is NOT PRIVATE, anyone else can see
   it and update the data in it.
#. Periodically we the data in MC3-DEMO with data from MC3 - when we do
   this your SANDBOX bank will disappear.

What information do I need to supply  to create a Sandbox objective bank?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are only two things you need to supply:

#. DisplayName = “Unique Name for your bank”
#. GenusType =
   mc3-objectivebank%3Amc3.learning.objectivebank.sandbox%40MIT-OEIT

==> The Display Name must be unique otherwise the POST will return the
existing sandbox bank with that name.

A Json example for creating a sandbox bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Issue a POST with that data to
`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks>`__

'{"displayName": {"text": "Your unique name here"}, "genusTypeId":
"mc3-objectivebank%3Amc3.learning.objectivebank.sandbox%40MIT-OEIT" }’

The following fields are optional

#. Description
#. DisplayText metadata fields are not processed when posting and the
   defaults for the bank are used.

#. formatTypeId
#. languageTypeId
#. scriptTypeId

A Python example for creating a sandbox bank
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 The bean may be fully configured following the template below (note the
genusTypeId):

        bank\_bean = {

                    '@type':'objectiveBankBean',

                    'id': '',

                    'current': True,

                    'description':{

                           
'formatTypeId':'Text+Formats%3Aplain%40okapia.net',

                            'languageTypeId':'639-2%3AEnglish%40ISO',

                            'scriptTypeId':'15924%3ALatin%40ISO',

                            'text': new\_class\_name

                    },

                    'displayName':{

                           
'formatTypeId':'Text+Formats%3Aplain%40okapia.net',

                            'languageTypeId':'639-2%3AEnglish%40ISO',

                            'scriptTypeId':'15924%3ALatin%40ISO',

                            'text': new\_class\_number

                    },

                   
'genusTypeId':'mc3-objectivebank%3Amc3.learning.objectivebank.sandbox%40MIT-OEIT'

            }

            mc3\_result = create\_objectivebank( bank\_bean )

Using a web library, you can then POST the bean to the url
‘/handcar/services/learning/objectivebanks/’. Our Python example is
below:

        def create\_objectivebank(bank\_bean):

        post\_args = bank\_bean

        url\_path = ('/handcar/services/learning/objectivebanks/')

        response = \_post\_request(url\_path, post\_args)

        return response.read()

def \_post\_request(url\_path, data\_map):

        connection = httplib.HTTPConnection(HOST)

        data = json.dumps(data\_map)

        connection.request('POST', url\_path, data, {'Content-Type':
'application/json'})

        return connection.getresponse()

You can create and update 3 kinds (types) of Objectives
-------------------------------------------------------

You can create three kinds of objectives:

#. Topic -- typically describes an area of knowledge to be learned --
   typically expressed as a noun
#. Outcome -- a specific outcome that is expected of the student --
   typically expressed as a verb
#. Generic Outcome -- an outcome that is inserted to link a  topic to an
   asset via a bloom type

See the above list of “Handy Dandy Types” for the values to use in the
genus type id.

Wait... What is a Generic Outcome again?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In some situations the faculty member does not want to author detailed
outcomes but still wants to attach assets to her topic via a bloom type.
They want to indicate that this asset could be used by the student to
“Learn” (a bloom type) the topic.

In this situation the Generic outcome should be constructed by using the
name of the bloom type prefixed to the name of the topic.  So if the
Topic is “Derivative” and the bloom type is the type for “Apply” then
the Generic Outcome name should be “Apply Derivative.”

What information do I need to supply to create a Topic?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Technically you do not need to supply ANY information except the bank id
as part of the url and the genus type inside the json object, but you
should include:

-  A name

-  The name does not HAVE to be UNIQUE but best practice is to not
   create duplicates to avoid confusion

-  optionally include a description

A JSON Example for creating a topic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Issue a POST with that data to
`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/ <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `mc3-objectivebank%3A1%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `/objectives <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__

'{"displayName": {"text": "Your topic name here"}, "genusTypeId":
"mc3-objective%3Amc3.learning.topic%40MIT-OEIT" }’

What information do I need to supply to create an Outcome?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Technically you do not need to supply ANY information except the bank id
as part of the url and the genus type inside the json object, but you
should include:

-  Description
-  Optionally you can assign a name or “code” so it can be referred to
   more succinctly,
-  Optionally you can categorize the outcome using the bloom types
   (grades).

-  Cognitive Process (Remember, Learn, Apply, Analyze, Create)
-  Knowledge Category (Factual, Procedural, Metacognitive, Conceptual)

-  Note: although Knowledge category is in the literature we have not
   seen much use of it to date.

A Json Example for creating an Outcome
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Issue a POST with that data to
`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/ <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `mc3-objectivebank%3A1%40MIT-OEI <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `T/objectives <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__

'{"description": {"text": "Your outcome here"}, "genusTypeId":
"mc3-objective%3Amc3.learning.outcome%40MIT-OEIT" }’

What information do I need to supply to create a Generic Outcome?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Technically you do not need to supply ANY information except the bank id
as part of the url and the genus type inside the json object, but you
should:

-  Make it a child of an existing topic
-  Assign it a name calculated by prepending the bloom type to the topic
   name
-  Assign it a description using the same calculation
-  Categorize the outcome using the bloom types (grades).

-  Cognitive Process (Remember, Learn, Apply, Analyze, Create)

A Json Example for creating an Outcome
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Issue a POST with that data to
`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/ <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `mc3-objectivebank%3A1%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `/objectives <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__

'{"description": {"text": "CALCULATED NAME HERE"}, "genusTypeId":
"mc3-objective%3Amc3.learning.generic.outcome%40MIT-OEIT",
"cognitiveProcessId":
"mc3.grade.system.cognitive.processes.bloom.revised%3Amc3.grade.bloom.learn%40MIT-OEIT"}’

How do I add the new GENERIC OUTCOME as a child to the topic?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To add the generic outcome as a child to the TOPIC to which it is
attached you should:

#. GET the child ids of the parent topic objective
#. Add the id of the generic outcome you just created to the list of ids
   you just got
#. POST it back updating the list of child ids

`http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/ <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/childids>`__\ `mc3-objectivebank%3A1%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `/childids <http://oki-dev.mit.edu/handcar/services/learning/objectivebanks/objectivebank%3A1%40MIT-OEIT/objectives/objective%3A1%40MIT-OEIT/childids>`__

A simple Javascript example for creating an objective
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/mc3\_testing/index.html <http://oki-dev.mit.edu/mc3_testing/index.html>`__

A more complete example in Python
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 It uses a set of http methods defined in an mc3\_http.py library:

        ##

# This module is a scratch space for experimenting with handcar POSTS,

# PUTS, DELETES, and potentially other things:

# From Jeff Merriman:

#
http://github.mit.edu/oeit/mc3-learning-adapter-py/blob/master/http\_tests.py

# Modified by Cole Shaw to return just the MC3 response

import urllib2

import urllib

import httplib

import json

from django.conf import settings

try:

    from collections import OrderedDict

except ImportError:

    from ordereddict import OrderedDict

   

from mc3\_learning\_adapter\_py.osid\_errors import NullArgument,
NotFound, IllegalState, OperationFailed, PermissionDenied, Unsupported

HOST = settings.MC3\_HOST

SERVICES = settings.MC3\_SERVICES

##

# This is where the work gets done to process GET requests with handcar.

# Here you can experiment with different libraries, etc.

def \_get\_request(url\_path):

        connection = httplib.HTTPConnection(HOST)

        connection.request('GET', url\_path)

        return connection.getresponse()

##

# This is where the work gets done to process POST requests with
handcar.

# Here you can experiment with different libraries, etc.

def \_post\_request(url\_path, data\_map):

        connection = httplib.HTTPConnection(HOST)

        data = json.dumps(data\_map)

        connection.request('POST', url\_path, data, {'Content-Type':
'application/json'})

        return connection.getresponse()

##

# This is where the work gets done to process PUT requests with handcar.

# Here you can experiment with different libraries, etc.

def \_put\_request(url\_path, data\_map):

        connection = httplib.HTTPConnection(HOST)

        data = json.dumps(data\_map)

        connection.request('PUT', url\_path, data, {'Content-Type':
'application/json'})

        return connection.getresponse()

##

# This is where the work gets done to process DELETE requests with
handcar.

# Here you can experiment with different libraries, etc.

def \_delete\_request(url\_path):

        connection = httplib.HTTPConnection(HOST)

        connection.request('DELETE', url\_path)

        return connection.getresponse()

def create\_objective(objective, bank\_id):

        post\_args = objective

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/objectives')

        response = \_post\_request(url\_path, post\_args)

        return response.read()

def create\_activity(activity, bank\_id, objective\_id):

        post\_args = activity

        post\_args['objectiveId'] = objective\_id

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/activities')

        response = \_post\_request(url\_path, post\_args)

        return response.read()

def update\_objective(objective, bank\_id):

        put\_args = objective

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/objectives')

        response = \_put\_request(url\_path, put\_args)

        return response.read()

def update\_activity(activity, bank\_id):

        put\_args = activity

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/activities')

        response = \_put\_request(url\_path, put\_args)

        return response.read()

def clear\_objective(objective\_id, bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/objectives/' + objective\_id)

        response = \_delete\_request(url\_path)

        return response.read()

def clear\_activity(activity\_id, bank\_id=OBJECTIVE\_BANK\_ID):

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/activities/' + activity\_id)

        response = \_delete\_request(url\_path)

        return response.read()

   

# NEW FROM COLE

def create\_activityasset(activityasset, bank\_id):

        post\_args = activityasset

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/activities/assetbased')

        response = \_post\_request(url\_path, post\_args)

        return response.read()

   

def create\_objectivebank(bank\_bean):

        post\_args = bank\_bean

        url\_path = ('/handcar/services/learning/objectivebanks/')

        response = \_post\_request(url\_path, post\_args)

        return response.read()

def get\_activity( activity\_id, bank\_id ):

        url\_path = ('/handcar/services/learning/objectivebanks/' +

                            bank\_id + '/activities/' + activity\_id)

        response = \_get\_request(url\_path)

        return response.read()

def get\_activities(objective\_id, bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/' +

                            bank\_id + '/objectives/' + objective\_id +
'/activities/')

        response = \_get\_request(url\_path)

        return response.read()

def get\_asset(asset\_id, bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/' +

                            bank\_id + '/assets/' + asset\_id)

        response = \_get\_request(url\_path)

        return response.read()

def get\_assets(activity\_id, bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/' +

                            bank\_id + '/activities/' + activity\_id +
'/assets/')

        response = \_get\_request(url\_path)

        return response.read()

   

def get\_objective( objective\_id, bank\_id ):

        url\_path = ('/handcar/services/learning/objectivebanks/' +

                            bank\_id + '/objectives/' + objective\_id)

        response = \_get\_request(url\_path)

        return response.read()

   

def get\_objective\_children(objective\_id, bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/' +

                            bank\_id + '/objectives/' + objective\_id +
'/children')

        response = \_get\_request(url\_path)

        return response.read()

   

def get\_all\_assets(bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/assets/')

        response = \_get\_request(url\_path)

        return response.read()

   

def get\_all\_activities(bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/activities/')

        response = \_get\_request(url\_path)

        return response.read()

   

def get\_all\_objectives(bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/objectives/')

        response = \_get\_request(url\_path)

        return response.read()

   

def get\_root\_objectives(bank\_id):

        url\_path = ('/handcar/services/learning/objectivebanks/'+

                   bank\_id + '/objectives/roots')

        response = \_get\_request(url\_path)

        return response.read()

From a Python console, we can then import the library and create /
update / delete objectives (or activities, assets, banks, etc.).

>>> from mc3\_learning\_adapter\_py.mc3\_http import create\_objective,
clear\_objective, update\_objective, get\_objective,
get\_root\_objectives, get\_objective\_children

        >>> obj\_bank\_id = 'objectivebank%3A2%40MIT-OEIT' #Chem Bridge

        >>> get\_root\_objectives(obj\_bank\_id)

'[{"@type":"objectiveBean","id":"objective%3A265%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Buffers:
A study of Chemical
Equilibria"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Buffers:
A study of Chemical
Equilibria"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"},{"@type":"objectiveBean","id":"objective%3A320%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Electrochem
and
Redox"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Electrochem
and
Redox"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"},{"@type":"objectiveBean","id":"objective%3A446%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"MO
Theory"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"MO
Theory"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"},{"@type":"objectiveBean","id":"objective%3A400%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Waves
and
Particles"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Waves
and
Particles"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"}]'

        >>> # Note the above returns 4 root objectives for the Chemistry
Bridge bank

        >>> # Now let’s pick one objective, Buffers, and look at it in
more detail

        >>> obj\_id = 'objective%3A265%40MIT-OEIT'

        >>> get\_objective\_children(obj\_id, obj\_bank\_id)

'[{"@type":"objectiveBean","id":"objective%3A266%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Chemical-Equilibria
Overview"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Chemical-Equilibria
Overview"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"},{"@type":"objectiveBean","id":"objective%3A276%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"pH"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"pH"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"},{"@type":"objectiveBean","id":"objective%3A281%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Acids
and
Bases"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Acids
and
Bases"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"},{"@type":"objectiveBean","id":"objective%3A300%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Salts"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Salts"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"},{"@type":"objectiveBean","id":"objective%3A307%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Buffers"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Buffers"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"}]'

        >>> # Note that these are the 5 children objectives of Buffers

        >>> # If we keep drilling down, we eventually find a sub-sub-sub
objective with a cognitive process id

        >>> sub\_sub\_obj='objective%3A267%40MIT-OEIT'

        >>> get\_objective\_children(sub\_sub\_obj, obj\_bank\_id)

'[{"@type":"objectiveBean","id":"objective%3A268%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Describe
in words and symbols the meaning of equillibrium
Keq"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Definitions
Chemical Equilibria Overview outcome
1A1"},"genusTypeId":"mc3-objective%3Amc3.learning.outcome%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"mc3-relationship%3Amc3.lo.2.activity.bloom.learn%40MIT-OEIT","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"},{"@type":"objectiveBean","id":"objective%3A269%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Interpret
where equilibrium lies given that K>1, K=1,
K<1"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Definitions
Chemical Equilibria Overview outcome
1A2"},"genusTypeId":"mc3-objective%3Amc3.learning.outcome%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"mc3-relationship%3Amc3.lo.2.activity.bloom.apply%40MIT-OEIT","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"}]'

        >>> import json

>>> my\_obj = json.loads(get\_objective\_children(sub\_sub\_obj,
obj\_bank\_id))[0]

>>> # The above line gets us the first objective within the list that is
returned.

>>> # But what does the cognitiveProcessId of
mc3-relationship%3Amc3.lo.2.activity.bloom.learn%40MIT-OEIT mean? What
other options are there?

>>> get\_bank\_grades(obj\_bank\_id)

'[{"@type":"gradeBean","id":"mc3-relationship%3Amc3.lo.2.activity.bloom.remember%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Activity
with assets that allow the student to remember the learning
objective"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Remember"},"genusTypeId":"mc3-grade%3Amc3.grade%40BLOOM-ORIG","gradeSystemId":"mc3-grade-system%3Acognitiveprocesses%40BLOOM-ORIG","inputScoreEndRange":1,"inputScoreStartRange":1,"outputScore":1},{"@type":"gradeBean","id":"mc3-relationship%3Amc3.lo.2.activity.bloom.learn%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Activity
through which a person may learn the concept or
objective"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Learn"},"genusTypeId":"mc3-grade%3Amc3.grade%40BLOOM-ORIG","gradeSystemId":"mc3-grade-system%3Acognitiveprocesses%40BLOOM-ORIG","inputScoreEndRange":2,"inputScoreStartRange":2,"outputScore":2},{"@type":"gradeBean","id":"mc3-relationship%3Amc3.lo.2.activity.bloom.apply%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Activity
through which a person may learn to apply the concept or
objective"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Apply"},"genusTypeId":"mc3-grade%3Amc3.grade%40BLOOM-ORIG","gradeSystemId":"mc3-grade-system%3Acognitiveprocesses%40BLOOM-ORIG","inputScoreEndRange":3,"inputScoreStartRange":3,"outputScore":3},{"@type":"gradeBean","id":"mc3-relationship%3Amc3.lo.2.activity.bloom.evaluate%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Activity
through which a person may learn to evaluate the concept or
objective"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Evaluate"},"genusTypeId":"mc3-grade%3Amc3.grade%40BLOOM-ORIG","gradeSystemId":"mc3-grade-system%3Acognitiveprocesses%40BLOOM-ORIG","inputScoreEndRange":4,"inputScoreStartRange":4,"outputScore":4},{"@type":"gradeBean","id":"mc3-relationship%3Amc3.lo.2.activity.bloom.analyze%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Activity
through which a person may learn to analyze the concept or
objective"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Analyze"},"genusTypeId":"mc3-grade%3Amc3.grade%40BLOOM-ORIG","gradeSystemId":"mc3-grade-system%3Acognitiveprocesses%40BLOOM-ORIG","inputScoreEndRange":5,"inputScoreStartRange":5,"outputScore":5},{"@type":"gradeBean","id":"mc3-relationship%3Amc3.lo.2.activity.bloom.create%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Activity
through which a person may learn to create new things based on the
concept or
objective"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Create"},"genusTypeId":"mc3-grade%3Amc3.grade%40BLOOM-ORIG","gradeSystemId":"mc3-grade-system%3Acognitiveprocesses%40BLOOM-ORIG","inputScoreEndRange":6,"inputScoreStartRange":6,"outputScore":6}]'

>>> # We can see that there are six types (to see this more easily, but
the output into something like
`http://json.parser.online.fr/ <http://json.parser.online.fr/>`__, but
take out the leading and trailing ‘ character.

>>> # Now let’s say we think this is actually a learn type instead of
remember. We change the object and update it in MC3

        >>> my\_obj['displayName']['text']

u'Definitions Chemical Equilibria Overview outcome 1A1'

        >>> my\_obj['displayName']['text'] = unicode('This is my new
outcome')

>>> my\_obj['displayName']['text']

u'This is my new outcome'

>>> update\_objective(my\_obj, obj\_bank\_id)

'{"@type":"objectiveBean","id":"objective%3A268%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Describe
in words and symbols the meaning of equillibrium
Keq"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"This
is my new
outcome"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"}'

>>> # Now, if you check online, the outcome display name has changed in
MC3!

>>> # Now let’s decide to delete this outcome...we don’t think it is
appropriate.

>>> delete\_me = my\_obj['id']

>>> delete\_me

u'objective%3A268%40MIT-OEIT'

>>> clear\_objective(delete\_me, obj\_bank\_id)

'{"@type":"objectiveBean","id":"objective%3A268%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Describe
in words and symbols the meaning of equillibrium
Keq"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"This
is my new
outcome"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"}'

>>> # We can now verify that in MC3, this objective no longer appears

>>> get\_objective\_children(sub\_sub\_obj, obj\_bank\_id)

'[{"@type":"objectiveBean","id":"objective%3A269%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Interpret
where equilibrium lies given that K>1, K=1,
K<1"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Definitions
Chemical Equilibria Overview outcome
1A2"},"genusTypeId":"mc3-objective%3Amc3.learning.outcome%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"mc3-relationship%3Amc3.lo.2.activity.bloom.apply%40MIT-OEIT","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"}]'

>>> # Oops, let’s add it back before anyone notices

>>> create\_objective(my\_obj, obj\_bank\_id)

'{"@type":"objectiveBean","id":"objective%3A11985%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Describe
in words and symbols the meaning of equillibrium
Keq"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"This
is my new
outcome"},"genusTypeId":"mc3-objective%3Amc3.learning.topic%40MIT-OEIT","assessmentId":"","cognitiveProcessId":"","knowledgeCategoryId":"","objectiveBankId":"objectivebank%3A2%40MIT-OEIT"}'

>>> # Notice that the ID is different than before even though we passed
it the previous object--this probably broke all sorts of activity /
asset and prerequisite relationships…

If the Objective is successfully created, the new Objective Bean is
returned with its newly assigned ID.

Creating and Updating Activities
--------------------------------

What is the minimum information needed to create an activity?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The only information that is required is:

#. Objective Id to which the activity is bound
#. genus type of the activity

Optional Fields:

#. DisplayName -- a name for the activity
#. Description -- a description of the activity
#. Ids of assets used in the activity

Issue a POST to

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/ <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `mc3-objectivebank%3A1%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `/activities <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__

'{"objectiveId": "mc3-objective%3A1%40MIT-OEIT","genusTypeId":
"mc3-activity%3Amc3.learning.activity.asset.based%40MIT-OEIT"}'

Creating a Generic Activity
~~~~~~~~~~~~~~~~~~~~~~~~~~~

A generic activity is similar to a regular activity except it indicates
that the author did not wish to explicitly name the activity.  This
occurs often where the activities are assumed to be that the student
would consume some sort of asset, watch video or read a web page.  If
this is the case you should use the speciay type

mc3-activity%3Amc3.learning.activity.generic%40MIT-OEIT

You might also wish to add a name that is calculated as follows:

“Do “ + asset.displayName

A Javascript example
~~~~~~~~~~~~~~~~~~~~

`http://oki-dev.mit.edu/mc3\_testing/index.html <http://oki-dev.mit.edu/mc3_testing/index.html>`__

If the Activity is successfully created, the new Activity Bean is
returned with its newly assigned ID.

A Python Example
~~~~~~~~~~~~~~~~

Using the same mc3\_http Python library from the Objective
Administration section, we can also see how to create, update, and
delete activities. Since many activities are attached to URLs, we create
them as “Asset-based Activities”, instead of separate Asset and
Activities--we let MC3 handle this behind the scenes.

>>> from mc3\_learning\_adapter\_py.mc3\_http import
create\_activityasset, clear\_activity, update\_activity, get\_activity,
get\_all\_activities

>>> obj\_bank\_id = 'objectivebank%3A1%40MIT-OEIT'

>>> get\_all\_activities(obj\_bank\_id)

>>> # This returns a ton of activities...so you don’t want to see them
here. But let’s take one and play with it

>>> act\_id = 'activity%3A1%40MIT-OEIT'

>>> get\_activity(act\_id, obj\_bank\_id)

'{"@type":"activityBean","id":"activity%3A1%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"A
Wikipedia: Antiderivative
Activity."},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Wikipedia:
Antiderivative"},"genusTypeId":"mc3-activity%3Amc3.learning.activity.asset.based%40MIT-OEIT","assessmentIds":[],"assetIds":["activity%3A1%40MIT-OEIT"],"courseIds":[],"objectiveId":"objective%3A1%40MIT-OEIT"}'

>>> my\_act = json.loads(get\_activity(act\_id, obj\_bank\_id))

>>> my\_act

{u'objectiveId': u'objective%3A1%40MIT-OEIT', u'displayName': {u'text':
u'Wikipedia: Antiderivative', u'languageTypeId':
u'639-2%3AEnglish%40ISO', u'scriptTypeId': u'15924%3ALatin%40ISO',
u'formatTypeId': u'Text+Formats%3Aplain%40okapia.net'}, u'description':
{u'text': u'A Wikipedia: Antiderivative Activity.', u'languageTypeId':
u'639-2%3AEnglish%40ISO', u'scriptTypeId': u'15924%3ALatin%40ISO',
u'formatTypeId': u'Text+Formats%3Aplain%40okapia.net'}, u'id':
u'activity%3A1%40MIT-OEIT', u'current': True, u'assessmentIds': [],
u'genusTypeId':
u'mc3-activity%3Amc3.learning.activity.asset.based%40MIT-OEIT',
u'courseIds': [], u'@type': u'activityBean', u'assetIds':
[u'activity%3A1%40MIT-OEIT']}

>>> # Again, let’s modify this. We can spice up the description a little
bit, since it reads almost the exact same as the display name

>>> my\_act['description']['text'] = unicode('Go read this amazing
Wikipedia article, curated by thousands of experts from around the
world')

>>> my\_act['description']['text']

u'Go read this amazing Wikipedia article, curated by thousands of
experts from around the world'

>>> update\_activity(my\_act, obj\_bank\_id)

'{"@type":"activityBean","id":"activity%3A1%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Go
read this amazing Wikipedia article, curated by thousands of experts
from around the
world"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Wikipedia:
Antiderivative"},"genusTypeId":"mc3-activity%3Amc3.learning.activity.asset.based%40MIT-OEIT","assessmentIds":[],"assetIds":["activity%3A1%40MIT-OEIT"],"courseIds":[],"objectiveId":"objective%3A1%40MIT-OEIT"}'

>>> # You can check this on MC3 that the description has changed!

>>> # Oops, we don’t want anyone to read it...let’s get rid of it

>>> delete\_me = my\_act['id']

>>> clear\_activity(delete\_me, obj\_bank\_id)

'{"@type":"activityBean","id":"activity%3A1%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Go
read this amazing Wikipedia article, curated by thousands of experts
from around the
world"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Wikipedia:
Antiderivative"},"genusTypeId":"mc3-activity%3Amc3.learning.activity.asset.based%40MIT-OEIT","assessmentIds":[],"assetIds":["activity%3A1%40MIT-OEIT"],"courseIds":[],"objectiveId":"objective%3A1%40MIT-OEIT"}'

>>> # Checking online, it is gone!

>>> # Let’s try to add it back (but with a new ID)

>>> # But because we want to add the activity with its URL, we should
create an Asset-based Activity, using a special bean called an
AssetActivity bean. This is the exact same as my\_act, but with one
additional “asset” key:value pair, where the value must be an asset
bean. I forgot to copy / download the asset previously, so let’s create
it from scratch. It should look like:

        {"@type":"assetBean",

"id":"",

"current":True,

"displayName":{

"formatTypeId":"Text+Formats%3Aplain%40okapia.net",

"languageTypeId":"639-2%3AEnglish%40ISO",

"scriptTypeId":"15924%3ALatin%40ISO",

"text":"Wikipedia: Antiderivative"},

"genusTypeId":"mc3-asset%3Amc3.learning.asset.url%40MIT-OEIT",

"assetContents":[{

"id":"",

"current":True,

"displayName":{

"formatTypeId":"Text+Formats%3Aplain%40okapia.net",

"languageTypeId":"639-2%3AEnglish%40ISO",

"scriptTypeId":"15924%3ALatin%40ISO",

"text":"Wikipedia: Antiderivative"},

"genusTypeId":"mc3-asset-content%3Amc3.learning.asset.content.unknown%40MIT-OEIT",

"assetId":"activity%3A2%40MIT-OEIT",

"url":"http://en.wikipedia.org/wiki/Antiderivative"}],

"canDistributeAlterations":False,

"canDistributeCompositions":False,

"canDistributeVerbatim":False,

"composition":False,

"compositionId":"",

"copyrightStatusKnown":False,

"providerLinkIds":[],

"publicDomain":False,

"published":False,

"title":{

"formatTypeId":"Text+Formats%3Aplain%40okapia.net",

"languageTypeId":"639-2%3AEnglish%40ISO",

"scriptTypeId":"15924%3ALatin%40ISO",

"text":"Wikipedia: Antiderivative"}}

>>> # Once we embed that into the activity bean, the result looks like
below:

>>> my\_act

{u'objectiveId': u'objective%3A1%40MIT-OEIT', u'displayName': {u'text':
u'Wikipedia: Antiderivative', u'languageTypeId':
u'639-2%3AEnglish%40ISO', u'scriptTypeId': u'15924%3ALatin%40ISO',
u'formatTypeId': u'Text+Formats%3Aplain%40okapia.net'}, u'description':
{u'text': u'Wikipedia: Antiderivative Activity', u'languageTypeId':
u'639-2%3AEnglish%40ISO', u'scriptTypeId': u'15924%3ALatin%40ISO',
u'formatTypeId': u'Text+Formats%3Aplain%40okapia.net'}, u'id': '',
u'current': True, u'assessmentIds': [], u'genusTypeId':
u'mc3-activity%3Amc3.learning.activity.asset.based%40MIT-OEIT',
u'courseIds': [], 'assets': {'canDistributeVerbatim': False,
'publicDomain': False, 'displayName': {'text': 'Wikipedia:
Antiderivative', 'languageTypeId': '639-2%3AEnglish%40ISO',
'scriptTypeId': '15924%3ALatin%40ISO', 'formatTypeId':
'Text+Formats%3Aplain%40okapia.net'}, 'copyrightStatusKnown': False,
'title': {'text': 'Wikipedia: Antiderivative', 'languageTypeId':
'639-2%3AEnglish%40ISO', 'scriptTypeId': '15924%3ALatin%40ISO',
'formatTypeId': 'Text+Formats%3Aplain%40okapia.net'}, 'compositionId':
'', 'assetContents': [{'displayName': {'text': 'Wikipedia:
Antiderivative', 'languageTypeId': '639-2%3AEnglish%40ISO',
'scriptTypeId': '15924%3ALatin%40ISO', 'formatTypeId':
'Text+Formats%3Aplain%40okapia.net'}, 'assetId': '', 'current': True,
'url': 'http://en.wikipedia.org/wiki/Antiderivative', 'genusTypeId':
'mc3-asset-content%3Amc3.learning.asset.content.unknown%40MIT-OEIT',
'id': ''}], 'id': '', 'current': True, 'providerLinkIds': [],
'genusTypeId': 'mc3-asset%3Amc3.learning.asset.url%40MIT-OEIT',
'published': False, 'composition': False, 'canDistributeAlterations':
False, '@type': 'assetBean', 'canDistributeCompositions': False},
u'@type': u'activityBean', u'assetIds': []}

>>> create\_activityasset(my\_act, obj\_bank\_id)

'{"@type":"activityBean","id":"activity%3A11250%40MIT-OEIT","current":true,"description":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Wikipedia:
Antiderivative
Activity"},"displayName":{"formatTypeId":"Text+Formats%3Aplain%40okapia.net","languageTypeId":"639-2%3AEnglish%40ISO","scriptTypeId":"15924%3ALatin%40ISO","text":"Wikipedia:
Antiderivative"},"genusTypeId":"mc3-activity%3Amc3.learning.activity.asset.based%40MIT-OEIT","assessmentIds":[],"assetIds":["activity%3A11250%40MIT-OEIT"],"courseIds":[],"objectiveId":"objective%3A1%40MIT-OEIT"}'

>>> # So we can see that creating it worked! It is back in the system
with a new ID.

Creating and Updating Assets
----------------------------

What is the minimum information needed to create an asset?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The only information that is technically required is the genus type of
the asset.  But you should supply the following:

#. displayName of the asset
#. genus type of the asset
#. genus type of the asset content
#. url of the asset content

Optional Fields:

#. Description of the asset
#. Description of the asset content
#. Additional asset contents if more than one resolution or variation of
   the asset exists

Issue a POST to

`https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/ <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `mc3-objectivebank%3A1%40MIT-OEIT <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__\ `/assets <https://oki-dev.mit.edu/handcar/services/learning/objectivebanks/mc3-objectivebank%3A1%40MIT-OEIT/objectives>`__

'{"genusTypeId":
"mc3-asset%3Amc3.learning.asset.url%40MIT-OEIT","assetContents":
[{"genusTypeId":
"mc3-asset-content%3Amc3.learning.asset.content.unknown%40MIT-OEIT"}]}'
