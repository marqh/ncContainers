NetCDF Containers Intentions
============================

The intent for NetCDF containers is to support semantics for typed containers of variables with named roles for NetCDF files.

The semantics will be suitable for use in NetCDF3 and NetCDF4 data models.

The semantic containers are a way of name spacing a NetCDF file, enabling multiple controlled vocabularies or conventions to be used without conflicts occurring.  They are intended to wrap variables which are defined using conventions such that further meaning may be attached.  

This wrapping is be done in such a way that applications and consumers who are unaware of the semantics may still utilise their known conventions terminology and choose to ignore the semantic container information.

.. Use Cases
.. ---------


.. Vectors
.. '''''''


.. Uncertainty
.. '''''''''''


Interoperability
----------------

NetCDF containers aim to provide a mechanism for flattening netCDF4 encoded files with groups into comprehensible netCDF3 classic data model files.



