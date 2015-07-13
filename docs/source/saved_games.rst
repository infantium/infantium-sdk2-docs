.. _progress-api:

.. warning:: NOT YET AVAILABLE

Saved Games API (cloud-saving)
==============================

Infantium provides cloud storage to save the progress of a player inside a content. Maybe
you want to save in which scene the player left the game or some item the player has achieved
during gameplay.

It doesn't matter if your content is developed to be run as an HTML5 page or as a native Android app.
By saving you game data in infantium cloud it will be instantly available among different devices
allowing player to start right where they left away the content without loosing content progress.

Infantium cloud-saving API also handles versioning the saved state data allowing for an easier
content updating mechanisms by simply writing a data migration function for each available update
if needed.


Serialize your data for storage
'''''''''''''''''''''''''''''''

Your content is responsible of serializing the incoming data and produce a byte array as the saved
data that will be saved in Infantium cloud services. We encourage developers to use some serializing
libraries like protocol buffers or gson.

Java:
    - https://code.google.com/p/google-gson/
    - https://developers.google.com/protocol-buffers/

XML serializer for Java:
    - http://simple.sourceforge.net/

Unity:
    - https://github.com/jacobdufault/fullserializer

After your data gets serialized, get an instance of `SavedGames` object by passing the same `Connection`
object used when creating the `WalkerManager` and implement the callbacks for saving response.
Then just call `saveData` with your serialized data. If there's no internet connection or some error
is produced meanwhile a `saveData` call is performed `savingError` will be triggered with the reason
for save failure. If everything works fine, you must expect a `savingCompleted` method call.


.. code-block:: java

    // Connect to infantium servers
    Server beta = Server.getBeta();
    Connection c = new Connection(beta, getInstrumentation().getContext());

    // Create a saved game instance with its corresponding callbacks
    SavedGames saver = SavedGames.getInstance(c, new SavedGames.SavedGamesInterface() {
        @Override
        public void savingCompleted(String response) {
            assertEquals(response, "OK");
        }

        @Override
        public void savingError(String status) {
            fail();
        }
    });

    // Save some test string
    saver.saveData("some test string".getBytes());



Content update on saved games
'''''''''''''''''''''''''''''

Writing a progress update is easy, you just only need to notify Infantium SDK of your
version dependent migration function and it will perform the migration if needed when
a player requires it.


