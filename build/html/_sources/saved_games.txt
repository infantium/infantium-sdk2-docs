.. _progress-api:

.. warning:: NOT PRODUCTION READY

Saved Games API (cloud-saving)
==============================

Infantium provides cloud storage to save the progress of a player inside a content. Maybe
you want to save in wich scene the player left the game or some item the player has achieved
during gameplay.

It doesn't matter if your content is developed to be run as an HTML5 page or as a native Android app.
By saving you game data in infantium cloud it will be instantly avaliable among different devices
allowing player to start right where they left away the content without loosing content progress.

Infantium cloud-saving API also handles versioning the saved state data allowing for an easier
content updating mechanisms by simply writing a data migration function for each avaliable update
if needed.


Serialize your data for storage
'''''''''''''''''''''''''''''''

Your content is responsible of serializing the incoming data and produce a byte array as the saved
data that will be saved in infantium cloud services. We encourage developers to use some serializing
libraries like protocol buffers or gson.

Java:
    - https://code.google.com/p/google-gson/
    - https://developers.google.com/protocol-buffers/

XML serializer for Java:
    - http://simple.sourceforge.net/

Unity:
    - https://github.com/jacobdufault/fullserializer

Migrating Saved Games
'''''''''''''''''''''

Writing a progress update is easy, you just only need to notify infantium SDK of your
version dependent migration fucntion and it will perform the migration if needed when
a player requires it.


