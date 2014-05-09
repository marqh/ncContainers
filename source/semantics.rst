Semantic Containers
===================

Semantic containers group NetCDF variables together and provide a named role for each contained variable.

Types of semantic container with clearly mandated roles can be defined by conventions authorities.


Container Vocabulary
--------------------

A new terminology is defined, a `container_type`.  This may be used to indicate that a particular set of container semantics are being used.

It is highly recommended that the 'value' of the container_type attribute is a URI, providing explicit resolution of the associated semantics for named roles and attributes.  `container_type` identifiers may be used to register a new container type and reference associated semantics.

NetCDF semantic containers does not define extended semantics for defined types, it merely provides the mechanism for others to do so.  A `simple` type is defined (hopefully this will be defined by a netCDF semantic containers owned URI in the future). This defines no further controlled semantics attributes.

.. A second new terminology is defined: a `member_role`.  This enables individual members of a container to take on semantic roles within the file.  The `simple` container type supports only one value for `member_role`, which is `member`.


Communities may define their own `container_type` values and within this scope define a controlled set of semantics for attribute names and allowable values to allow rich semantic content to be provided.

A container type may define container roles.  These are attribute names which enable a particular member to be explicitly linked via a named role, with associcated semantics, defined by the container type.  Container roles link directly to variables within the scope of the container.  All container role attribute names must be prepended with the string `container_role_` to enable identification by software.




