
===========
Unity Guide
===========

Unity Example
'''''''''''''

Inside .unitypackage there is a simple project example that contains all avaliable SDK2 function calls. Please refer to it for C# syntax.



Traverse the graph
''''''''''''''''''

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

.. code-block:: c#

    // Set score of player
	BasicScoring s = infantium.getScorer<BasicScoring> ();
	s.success ();
	s.fail ();
	s.neutral ();
	
	// Evaluate the terminal node
	infantium.evaluate ();


Activate Infantium Shaker
'''''''''''''''''''''''''

.. code-block:: c#

	// Start infantium shaker :)
	infantium.startShaker ();

