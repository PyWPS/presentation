************
Introduction
************

What is PyWPS
-------------

    * PyWPS is an implementation of the `Web Processing Service standard`_
      from the `Open Geospatial Consortium`_ 
    * PyWPS is written in `Python`_
    * Started in the Spring of 2006
    * Supports all available tools in Python for geospatial operations
    * http://pywps.org


What PyWPS is *NOT*
-------------------

    * complicated
    * a client
    * a GUI
    * a server with pre-installed processes

**************************
OGC Web Processing Service
**************************
    
The OGC Web Processing Service
------------------------------

   * OGC open web standard for remote geo-spatial processing.
   * Integrated with web data services: **WFS**, **WCS**.
   * Three basic requests:
   
      * *GetCapabilities*
      * *DescribeProcess*
      * *Execute*
      
   * Three basic input/output classes:
   
      * *Literal*
      * *Complex* - for geo-spatial data and services
      * *BoundingBox* - for geo-spatial data extent

The OGC Web Processing Service
------------------------------

.. image:: images/WPS.png
   :align: center
   :width: 1000
      
http://www.slideshare.net/TheodorFoerster/restful-web-processing-service
      
      
Essential PyWPS Functionality
-----------------------------

   * Communication bridge with WPS.
   * Fetches input data referenced in *Execute* requests.
   * Creates a container for the process instance.
   * Process management: communication, reporting, logging.
   * Data storage for final data outputs.
   * Client notification and status reporting.
   


.. _`Web Processing Service standard`: http://opengeospatial.org/standards/wps
.. _`Open Geospatial Consortium`:  http://opengeospatial.org
.. _`Python`: https://python.org

