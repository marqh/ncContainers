NetCDF3 Encoding
================

In the NetCDF3 classic data model, semantic containers are encoded using container variables.  Container variables are identified by their use of the attribute `container_type` and their lack of any data.  A container variable may not reference any dimensions nor contain any data payload.

A NetCDF3 specific attribute is defined, `container_members`, which is only valid if used with a container variable.  This contains a space separated list of variable names which exist is the file.

.. In order to provide roles for variables, each variable pointed to by the `container_members` attribute may be a container role variable.  In this case the variable is required not to reference any dimensions nor contain any data payload.  Each of these variables will have the attribute `variable_role` defined once.  `variable_role` has a controlled vocabulary, defined by the scope of the `container_type`.

.. For role variables, the NetCDF3 specific attribute `container_members` is used to provide a space separated list of variable names which exists within the file.  In many cases a role will be a singleton role, in which case the `container_variable` will be limited to a single variable name.

Specific container types may define attributes which reference variables within the scope of the semantic group, those referenced by the `container_members` attribute, enabling variables, inculding further semantic container variables to be given specific roles within the scope of the semantic container.


Variable Names
''''''''''''''

The variable name of a container variable name is a convenient string to use for disambiguation of variable names in netCDF3 files.  The containing variable's name may be prepended to the contained variable's name, linked by a triple underscore `___`.

Degeneracy
----------

There is a degenerate case where the `container_type` is defined as `simple` and no roles are defined.

In this case, the semantic container variable is semantically identical to a standard NetCDF 4 group.  Interchange between these encodings does not change the meaning of the metadata at all.

When transforming to netCDF4 encoding, amended variable names will be stripped of their leading container names if used.  These are identified by the triple underscore.
