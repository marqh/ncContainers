Semantic Containers
===================

Semantic containers group NetCDF variables together and provide a named role for each contained variable.

Types of semantic container with clearly mandated roles can be defined by conventions authorities.


Container Vocabulary
--------------------

A new attribute name is defined `container_type`.  This attribute may be used to indicate that a particualr set of container semantics are being used.

It is highly recommended that the 'value' of the container_type attribute is a URI, providing explicit resolution of the associated semantics for named roles and attributes.  `container_type` identifiers may be used to register a new container type and reference associated semantics.

NetCDF containers does not define extended semantics for defined types, it merely provides the mechanism for others to do so.  A `simple` type is defined (hopefully this will be defined by a netCDF containers owned URI in the future. 

A new attribute name is defined: `variable_role`.  This attribute enables individual members of the container to take on semantic roles within the file.  The `simple` container type supports only one value for `variable_role`, which is `member`.





