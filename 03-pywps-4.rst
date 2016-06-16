*******
PyWPS-4
*******
   
Motivation for PyWPS-4
----------------------

   * PyWPS is now a decade old.
   * Python version 3 taking over.
   * New bindings for other libraries (e.g GRASS).
   * New data formats (e.g. GeoJSON, KML, TopoJSON).
   * Version 2.0 of the WPS standard.
   * Less restrictive licence (MIT).
   
   
New Technologies
----------------

   * lxml
   * Flask / Werkzeug
   * WSGI
   * Multiprocessing
   * PyPy
   * Jython
   * OWSLib
   
   
Data Validation
---------------

   * A four step approach:
      -  ***No validation*** - always considered valid.
      -  ***Simply validation*** - uses just the *mimeType*.
      -  ***Strict validation*** - attempts to open *Complex* inputs with GDAL, comparing with *mimeType*.
      -  ***Very strict validation*** - uses an XML schema.

   * Plus custom validation, already including:
      . ESRI Shapefile
      . GeoJASON
      . GML
      . GeoTIFF
      
      
Process Containerising
----------------------

   * WPS server should run *Execute* requests concurrently.
      . but in totally insulated fashion;
      . no shared resources or data.
   * PyWPS-3:
      . a temporary folder is created for each *Execute*;
      . resulting data is moved to publishing folder;
      . temporary folder is deleted at execution end.
   * PyWPS-4 aims at a safer approach:
      . Docker
      . vagrant
      . ...

      
Asynchronous Execution
----------------------

   * PyWPS can process various *Execute* requests in parallel:
      . configurable number;
      . plus a queue of waiting requestes.
   * PyWPS-4 now uses the Python *Multiprocessing* module:
      . *os.fork()* abandoned;
      . PyWPS now runs on Windows too.
   * Process metadata now stored in a local SQLite database:
      . logging;
      . *Execute* request queueing.
      . WPS 2.0 functionality to pause and resume processes.
      
      
Future Work
-----------

   * New requests in WPS 2.0: *Pause*, *Release*, *Delete*.
   * Improved security with process containerising.
   * Administrative web interface.
   * External services to publish outputs.
   * Support for other languages beyond English.