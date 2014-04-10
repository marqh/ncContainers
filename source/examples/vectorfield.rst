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
       int     lat(lat), lon(lon), time(time);
       float     dxaptg(time,lat,lon);
       float     dyaptg(time,lat,lon);
       float     daptmagg(time,lat,lon);
       float     daptdirg(time,lat,lon);
       int       vectorfield ;
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       time:units = "seconds";
       rh:_FillValue = -1;
       
       vectorfield:container_type = "http://vectorfieldsemantics.notauri.net/vectorfield" ;
       vectorfield:members = "dxapt dyapt daptmag daptdir"
       vectorfield:i_component = dxaptg ;
       vectorfield:j_component = dyaptg ;
       vectorfield:magnitude = daptmagg ;
       vectorfield:direction = daptdirg ;
       vectorfield:base_phenomenon = 'air_potential_temperature' ;
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
       int     lat(lat), lon(lon), time(time);
       float     dxaptg(time,lat,lon);
       float     dyaptg(time,lat,lon);
       float     daptmagg(time,lat,lon);
       float     daptdirg(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       time:units = "seconds";
       rh:_FillValue = -1;
       
       :container_type = "http://vectorfieldsemantics.notauri.net/vectorfield" ;
       :i_component = dxaptg ;
       :j_component = dyaptg ;
       :magnitude = daptmagg ;
       :direction = daptdirg ;
       :base_phenomenon = 'air_potential_temperature' ;
       :base_units = 'K'
       
     }
     
     }
