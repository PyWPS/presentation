*******
Example
*******

Installing
----------

.. code-block:: bash

	# Checkout *pywps*
	git clone git@github.com:geopython/pywps.git pywps

	# Checkout *pywps-demo*
	git clone git@github.com:geopython/pywps-demo.git pywps-demo

	# Install dependencies (*requirements.txt*)
	cd pywps && pip install -r requirements-dev.txt

	# Install pywps
	sudo python setup.py install

	# Run the demo server
	cd ../pywps-demo && python demo.py 


Folder structure
----------------

.. code-block:: bash

   pywps
   pywps-demo
   +-- demo.py
   +-- LICENCE.txt
   +-- processes          <- working folder
   |   +-- area.py
   |   +-- bboxinout.py
   |   `-- ...
   +-- pywps.cfg          <- configurations
   +-- requirements.txt
   +-- server.py          <- run server
   +-- setup.py
   +-- static
   +-- templates
   `-- tests


Process structure
-----------------

.. code-block:: Python

   from pywps import Process, ComplexInput, LiteralOutput, ...
   
   class Area(Process):
       def __init__(self):
           inputs = [ComplexInput('layer', 'Layer', ... 
           outputs = [LiteralOutput('area', 'Area', ...
           super(Area, self).__init__(
               self._handler,
               identifier='area',
               title='Process Area',
               inputs=inputs,
               outputs=outputs,
               store_supported=True,
               status_supported=True)
       def _handler(self, request, response):
        

The handler method
------------------

.. code-block:: Python

    def _handler(self, request, response):
        from shapely.geometry import shape
        with temp_dir() as tmp:
            input_gml = request.inputs['layer'].file
            input_geojson = os.path.join(tmp, 'input.geojson')
            subprocess.check_call(['ogr2ogr', '-f', 'geojson',
                                   str(input_geojson), input_gml])
            with open(input_geojson, 'rb') as f:
                data = json.loads(f.read())
            for feature in data['features']:
                geom = shape(feature['geometry'])
                feature['area'] = geom.area
            response.outputs['area'].data = [feature['area'] ...
            return response



.. |hbar| unicode:: 01C0 .. 
