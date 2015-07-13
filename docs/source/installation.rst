================
SDK Installation
================

Currently only following platforms are supported by Infantium SDK:

* Android Native
* Unity for Android

The following platforms are going to be released soon:

* Javascript
* Unity for HTML5
* iOS


Android Gradle
''''''''''''''

To install the Infantium SDK v2 follow those steps:

1. Inside Android Studio, edit the root :code:`build.gradle` file
3. Copy Infantium android .aar file and .jar with dependencies inside your libs directory of your project.
2. Ensure all android archives and jar files from libs directory are being included in project

.. code-block:: none

    dependencies {
        ...
        compile fileTree(dir: 'libs', include: ['*.jar','*.aar'])
        ...
    }


Unity Android
'''''''''''''

Download the .unitypackage plugin and import all contents from the package to your unity project.
Then after importing the data into your unity project nto your unity project create a directory
named :code:`Streaming Assets` inside :code:`Assets` folder of your project. Unity make accessible the files
placed inside this directory into the normal filesystem of target machine. We will use this
capability to put the :ref:`content-graph` file that the native android plugin will read from.
Rename your :ref:`content-graph` file to :code:`inf_graph.graphml` and make sure is in the root of
"Streaming Assets" dir.

Yuu must configure minimum API level in unity to be at least 14 to ensure manifests of SDK and Unity
can be able to merge properly.