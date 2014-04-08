NetCDF4 Encoding
================

In NetCDF4's enhanced data model semantic containers are encoded using groups.

A root group is defined in any NetCDF4 file.  Each semantic container is defined as a new group.  A semantic container is identifiable by the use of the attribute `container_type`.

A semantic container group will reference role groups within the file, which use the attribute `variable_role` to define a role for a variable.  A semantic role group is a group which is contained within a semantic group and uses the attribute `variable_role`.



Degeneracy
----------

There is a degenerate case where the `container_type` is defined as `simple`, the `variable_role` definitions are all `member` and no further attributes are defined on any semantic role group instance.

In this case, the semantic container group is semantically identical to a standard NetCDF 4 group.  Interchange between these two encodings does not change the meaning of the metadata at all.
