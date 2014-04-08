NetCDF3 Encoding
================

In the NetCDF3 classic data model, semantic containers are encoded using container variables.  Container variables are identified by their use of the attribute `container_type` and there lack of any data.  A container variable may not reference any dimensions nor contain any data payload.

A NetCDF3 specific attribute is defined, `container_members`, which is only valid if used with a container variable.  This contains a space separated list of variable names which exist is the file.

Each variable pointed to by the `container_members` attribute is required not to reference any dimensions nor contain any data payload.  Each of these variables will have the attribute `variable_role` defined once.  `variable_role` has a controlled vocabulary, defined by the scope of the `container_type`.

Another NetCDF3 specific attribute is defined, `container_variable` which will have a space separated list of variable names which exists within the file.  In many cases a role will be a singleton role, in which case the `container_variable` will be limited to a single variable name.

Degeneracy
----------

There is a degenerate case where the `container_type` is defined as `simple`, the `variable_role` definitions are all `member` and no further attributes are defined on any variable identified as a `container_member` instance.

In this case, the semantic container variable is semantically identical to a standard NetCDF 4 group.  Interchange between these two encodings does not change the meaning of the metadata at all.
