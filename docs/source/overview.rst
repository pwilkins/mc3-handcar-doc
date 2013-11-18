========
Overview
========

This handcar service supports a restful JSON interface to the MC3
system's learning objectives.  Handcar uses
`Moxy <http://wiki.eclipse.org/EclipseLink/Examples/MOXy/MOXy_JSON_Provider>`__\ to
serialize the objects into JSON.

Known issues/Issues under consideration for implementation in future releases
-----------------------------------------------------------------------------

These items are known issues that are under consideration for
implementation in future releases.

#. Free form querying using keywords to find objectives is not supported
#. Managing the configuration data for a bank directly via Handcar
#. Providing a metadata so the UI can dynamically validate data values
#. Support for assessments
#. Managing assets directly via a separate repository service
#. Support for additional asset content types (mime types)
#. You cannot store additional information such as name, description or
   extensions on Parent-Child relationships
#. Getting branding information about a bank or an asset is not yet
   supported
#. Cross bank relationships will not be blocked in all situations but
   they are not fully supported as many details remain to be worked out.

Other Related Documentation
---------------------------

Detailed documentation on all of the methods and data elements is
contained in “Contract Docs” which fully explain the contract.

See
`http://oki-dev.mit.edu/handcar/contractdocs/ <http://oki-dev.mit.edu/handcar/contractdocs/>`__

--------------

Model Diagram
-------------

.. image:: images/image01.png

Model Description
-----------------

Banks contain three main types of objects:

-  `Objectives <#h.pzxzpdsydj9e>`__-- Learning Objectives which come in
   three distinct types:

-  Topics -- also called concepts which define an area of knowledge ,
   typically expressed as NOUNS
-  Outcomes -- which are specific learning goals, typically expressed
   starting with VERBS
-  Generic Outcomes -- which are outcomes that hold no real data
   themselves but are there to simply tie together topics and content
   via a bloom type -- For example if the topic is “Derivative” a
   generic outcome could be “Learn Derivative”

-  `Activities <#h.bycu3aaffge7>`__ which are tied to objectives - that
   a student may do in order to master the objective
-  `Assets <#h.h08m2wx23t1l>`__ which are tied to activities -- that are
   typically the content that a student consumes as part of the activity

-  In the model a single asset have multiple “Asset Contents” which may
   be different resolutions of the same asset, for example the same
   asset can have a thumbnail representation and full size JPG versions
   of the same picture.

-  `Relationships <https://oki-dev.mit.edu/handcar/contractdocs/RelationshipBean.html>`__ --
   Alternative View of Relationships between objectives, see `The
   Relationship Service <#h.cf029iro3bkl>`__

Additionally there are configuration “types” and “grade scales” used to
organize and categorize these three main objects.

For a detailed description of each of these objects and data fields see
the `Contract
Documentation <http://oki-dev.mit.edu/handcar/contractdocs/>`__
