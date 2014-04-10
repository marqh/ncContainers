NetCDF4 Encoding
================

In NetCDF4's enhanced data model semantic containers are encoded using groups.

A root group is defined in any NetCDF4 file.  Each semantic container is defined as a new group.  A semantic container is identifiable by the use of the attribute `container_type`.

.. A semantic container group will reference role groups within the file, which use the attribute `member_role` to define a role for a variable.  A semantic role group is a group which is contained within a semantic group and uses the attribute `member_role`.

Specific container types may define attributes which reference groups and variables within the scope of the semantic group, enabling variables and groups to be given specific roles within the scope of the semantic container.


Degeneracy
----------

In the degenerate case, where the `container_type` is defined as `simple`, the semantic container group is semantically identical to a standard NetCDF 4 group.  Interchange between these two encodings does not change the meaning of the metadata at all.
