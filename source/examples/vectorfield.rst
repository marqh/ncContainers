Vector Field
============

A vector field may be represented by a set of scalar fields with clearly defined roles defining these scalar fields as components of the vector field.

Each scalar field may be defdined using well known CF semantics, for example the CF conventions for NetCDF files.

NetCDF3 Encoding
----------------


::

     netcdf vfield {
     
     dimensions:
     lat = 10, lon = 5, time = unlimited;
     
     
     
     variables:
       float lat(lat) ;
         lat:units = "degrees_north";
       
       float lon(lon) ;
         lon:units = "degrees_east";
       
       float time(time);
         time:units = "seconds";
       
       float     dxaptg(time,lat,lon);
       float     dyaptg(time,lat,lon);
       float     daptmagg(time,lat,lon);
       float     daptdirg(time,lat,lon);

       int       vectorfield ;
         vectorfield:container_type = "http://vectorfieldsemantics.notauri.net/vectorfield" ;
         vectorfield:container_members = "dxapt dyapt daptmag daptdir"
         vectorfield:container_role_i_component = dxaptg ;
         vectorfield:container_role_j_component = dyaptg ;
         vectorfield:container_role_magnitude = daptmagg ;
         vectorfield:container_role_direction = daptdirg ;
         vectorfield:base_phenomenon = 'air_potential_temperature horizontal gradient' ;
         vectorfield:base_units = 'K'
       
     }
     
     }


NetCDF4 Encoding
----------------

::

     netcdf vfield {
     
     dimensions:
     lat = 10, lon = 5, time = unlimited;
     
     group vectorfield {
     
     variables:
       float lat(lat) ;
         lat:units = "degrees_north";
       
       float lon(lon) ;
         lon:units = "degrees_east";
       
       float time(time) ;
         time:units = "seconds";
       
       float     dxaptg(time,lat,lon);
       float     dyaptg(time,lat,lon);
       float     daptmagg(time,lat,lon);
       float     daptdirg(time,lat,lon);

       :container_type = "http://vectorfieldsemantics.notauri.net/vectorfield" ;
       :container_role_i_component = dxaptg ;
       :container_role_j_component = dyaptg ;
       :container_role_magnitude = daptmagg ;
       :container_role_direction = daptdirg ;
       :base_phenomenon = 'air_potential_temperature' ;
       :base_units = 'K'
       
     }
     
     }
