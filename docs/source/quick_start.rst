
=================
Quick Start Guide
=================


Content Graph File
''''''''''''''''''

The :ref:`content-graph` file holds info about the different cognitive aspects related to the
distribution of your content entities, such as scenes, levels, chapters, etc. To make the SDK
work you need to walk each node of the :ref:`content-graph` in and out synchronized with the
content entity that is shown to the user in realtime. To make the sync happen there are some calls
that will help to make the SDK know which part of the content is displaying and relate it to
:ref:`content-graph`.


Graph traversing
''''''''''''''''

In order to traverse the :ref:`content-graph` a graph manager object must be created. This manager
is responsible of handling events that outcome from Walker object. A WalkerManager object needs
a Connection object to send events to Infantium servers. WalkerManager handles the bootstrap of
Walker object automatically, you only need to specify the :ref:`content-graph` file as an InputStream. There
When with a native android project, copy the :ref:`content-graph` file into a directory named "raw" inside
the android resources folder, if the "raw" dir does not exist create it.
Create a Connection object with selected Infantium servers and initialize the WalkerManager.

.. code-block:: java

    Server beta = Server.getBeta();
    Connection c = new Connection(beta, getInstrumentation().getContext());

    // Get the graph file from resources
    InputStream f = getInstrumentation().getContext().getResources().openRawResource(R.raw.demograph);

    // Create the walker and assign the corresponding connection to infantium servers
    WalkerManager wm = new WalkerManager(c, f);

When a new user session is started the graph traversing resets and Walker points to ROOT node of
the :ref:`content-graph`. Starting from there, each time that there is a transition to a place
on content with different associated node a walk must be notified to SDK. The walk will be
validated for invalid jumps and if succeeded, walker will point to selected node_id.

.. code-block:: java

    // Get walker from walker manager
    Walker w = wm.getWalker();

    // Walk away from ROOT node to next connected node with id "Topic Scene"
    w.moveNext("Topic Scene");


Evaluate congitive nodes
''''''''''''''''''''''''

Some nodes of the :ref:`content-graph` have special properties that allow a cognitive aspect
of the content to be evaluated and sent to Infantium. To do that, look at the special id's of the
specific :ref:`content-graph` file for the content you are developing. The nodes labeled as
TERMINAL_NODE have associated an evaluation method that can be used from inside the SDK when walking
into that node using the "moveNext" function.

.. code-block:: java

    ...
    // Walk into a terminal node that uses BasicScorer as scoring method
    w.moveNext("<terminal_node_id>");
    ...

    ...
    // Now that we are on terminal node, instantiate a BasicScorer to evaluate it
    BasicScoring scorer = w.getScorer();
    ...

    ...
    // Evaluate stimuli
    scorer.success();
    ...

    ...
    // Send evaluation event before visiting next node
    w.evaluate();
    ...


The `evaluate` function can only be called once each time a node is visited, ensure it is called
before moving to next node to capture all evaluation events that happened when visiting node.



