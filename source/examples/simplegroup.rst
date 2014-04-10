Simple Container
================

This is an example of the degenerate case, where a group in netCDF4 is equivalent to a `simple` semantic container, which is equivalent to a NetCDF3 `simple` container.

All four of these examples are semantically identical and software should be able to transform data files between the encoding options at will.

NetCDF4 Group
-------------


::

     netcdf foo {    // example netCDF specification in CDL
     
     dimensions:
     lat = 10, lon = 5, time = unlimited;
     
     group instrument {
     
     variables:
       int     lat(lat), lon(lon), time(time);
       int     rh(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       time:units = "seconds";
       rh:_FillValue = -1;
     
       :measurement_platform = "aircraft"
     }
     group model {
     
     variables:
       int     lat(lat), lon(lon), time(time);
       int     rh(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       time:units = "seconds";
       rh:_FillValue = -1;
       
       :measurement_platform = "global circulation model"
     }
     
     }


Degenerate netCDF4 Semantic Group
---------------------------------


::

     netcdf foo {    // example netCDF specification in CDL
     
     dimensions:
     lat = 10, lon = 5, time = unlimited;
     
     group instrument {
     
     variables:
       int     lat(lat), lon(lon), time(time);
       int     rh(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       time:units = "seconds";
       rh:_FillValue = -1;
     
     :measurement_platform = "aircraft"
     :container_type = 'simple'
     }
     group model {
     
     variables:
       int     lat(lat), lon(lon), time(time);
       int     rh(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       time:units = "seconds";
       rh:_FillValue = -1;
       
     :measurement_platform = "global circulation model"
     :container_type = 'simple'
     
     }


Semantic Container NetCDF3 Classic
----------------------------------

::

     netcdf foo {    // example netCDF specification in CDL
     
     dimensions:
     lat = 10, lon = 5, time = unlimited;
          
     variables:
       int instrument ;

       int     instrument___lat(lat), instrument___lon(lon), instrument___time(time);
       int     instrument___rh(time,lat,lon);
     
       instrument___lat:units = "degrees_north";
       instrument___lon:units = "degrees_east";
       instrument___time:units = "seconds";
       instrument___rh:_FillValue = -1;
     
       instrument:measurement_platform = "aircraft" ;
       instrument:container_type = 'simple' ;
       instrument:members = "instrument___lat instrument___lon instrument___time" ;

       int model ;
     
       int     model___lat(lat), model___lon(lon), model___time(time);
       int     model___rh(time,lat,lon);
     
       model___lat:units = "degrees_north";
       model___lon:units = "degrees_east";
       model___time:units = "seconds";
       model___rh:_FillValue = -1;
       
       model:measurement_platform = "global circulation model" ;
       model:container_type = 'simple' ;
       model:members = "model___lat model___lon model___time" ;
     
     }
