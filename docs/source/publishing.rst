.. _content-publishing:

====================
Publish your content
====================

Content metadata
''''''''''''''''
There are some metadata that must be filled when creating a content inside infantium. Some of
the fields are required to maintain an index of content inside infantium, others are used for
information or promotion purposes. The required fields for a content are:

- Title
- Short Description (Limited to 140 characters)
- Large Description (Limited to 1000 characters)
- Language availability
- Target age

Content assets
''''''''''''''

The content assets are used inside infantium platform to provide better promotional coverage to
content publishing. Those assets can be used for promotional banners inside infantium app or on
content listing highlights. Even though it's optional to submit those assets, it is recommended
and can improve the visibility of your content inside infantium.


Publishing phases
'''''''''''''''''

A content that is inside infantium platform shall pass every phase in this list. All phases are
mandatory and define the relationship between Infantium and the publisher partner. In other words
this phases are a way to establish a way to ensure that all cognitive content integrated
is aprooved for infantium cognitive experts.


0. Content Integration request
1. Cognitive pre-evaluation (Infantium)
    1.1. Content analysis & :ref:`content-graph` creation (Infantium)
2. SDK Integration inside content.
3. Content integration validation (Infantium)
4. Agreement, pricing, publishing and distribution.



Versioning the content
''''''''''''''''''''''
Each content in published state has an int version number. This int is incremented in 1 when a new
content version is published. Infantium SDK automatically performs cognitive data migration when no
changes are applied to :ref:`content-graph`. If infantium asks for an update in :ref:`content-graph`
the content will enter the pre-publish to ensure integration with new content graph is done properly.


Pricing your content
''''''''''''''''''''

Currently only europe is the target market for Infantium. Then you must introduce the price for
the app in euros, it will be automatically converted to local country currency for those european countries
not using euros. The pricing step selects a pricing tier in which the content will be published for final
public.


Publisher metadata
''''''''''''''''''

.. warning:: Content publishers must fulfill some company data before publishing content inside infantium.
    This data is private for Infantium and will only be used for internal communication purposes.

- Publisher Name
- Publisher Icon (200x200 image)
- Publisher Country
- Some business description
- Publisher Address
- Publisher email
- Publisher Website
    - [Optional] Twitter account
    - [Optional] Facebook Account
    - [Optional] G+ Account
- Contact Name
- Contact Phone
- Contact email
