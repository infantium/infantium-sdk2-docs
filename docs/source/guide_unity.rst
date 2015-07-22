
===========
Unity Guide
===========

This guide covers specific integration aspects for Unity developers. Please refer to main guide for full process covering.

Unity Example
'''''''''''''

Inside .unitypackage there is a simple project example that contains all avaliable SDK2 function calls. Please refer to it for C# syntax.


Traverse the graph
''''''''''''''''''

As in native Android development, to transverse the graph simply call to `moveNext(<node_id>)` with the specified node identification to move into.

.. code-block:: c#

	// Get infantium SDK singleton
	infantium = InfantiumUnityAndroid.getInstance();

	// Walk up to a terminal node
	infantium.moveNext("Topic Scene");
	infantium.moveNext("Welcome screen");
	infantium.moveNext("Alimentos");
	infantium.moveNext("memory");
		

Scoring a Terminal Node
'''''''''''''''''''''''

Score a terminal node is as easy as calling the fucntions from an instantiated score of a terminal node.

.. code-block:: c#

    // Set score of player
	BasicScoring s = infantium.getScorer<BasicScoring> ();
	s.success ();
	s.fail ();
	s.neutral ();
	
	// Evaluate the terminal node
	infantium.evaluate ();

Build and debug 
'''''''''''''''

To make the integration process we encourage developers to enable Development build when targeting the app for Android devices. This extends the android logcat with
helpful info with trace for errors on SDK2 Android bridge.

.. image:: _static/unity_build.png
   :alt: Remember to check Script Debugging and Development Build
   :align: center

To compile the app without errors while using the Unity Android plugin, required minimum api level is 14. To modify it click on "Player Settings..." button and modify it.

.. image:: _static/min_api_level.png
   :alt: Minimum API Level must be 14
   :align: center


To check for errors when integrating the Infantium plugin for Unity use the Android monitor tool that is provided withing android-sdk.

	$ cd <path_to_android_sdk>/tools/
	$ ./monitor

Inside the monitor you will see the connected devices, click your device to see logs incoming from that device. Then add a log filter by "Unity" tag.

Activate Infantium Shaker
'''''''''''''''''''''''''

In Unity, you can activate Infantium Shaker that allows users to cleanly go back to Infantium by shaking the device with the following API call:

.. code-block:: c#

	// Start infantium shaker :)
	infantium.startShaker ();

