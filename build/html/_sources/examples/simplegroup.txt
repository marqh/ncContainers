Simple Container
================

This is an example of the degenerate case, where a group in netCDF4 is equivalent to a `simple` semantic container, which is equivalent to a NetCDF3 `simple` container.

All four of these examples are semantically identical and software should be able to transform data files between the encoding options at will.


Semantic Container NetCDF3 Classic
----------------------------------

::

     netcdf foo {    // example netCDF specification in CDL
     
     dimensions:
     instrument___lat = 10, instrument_lon = 5, time = unlimited
          model___lat = 17, model_lon = 9
     variables:
       int instrument ;
       time(time)
       int     instrument___lat(instrument___lat), instrument___lon(instrument___lon);
       int     instrument___rh(time,instrument___lat,instrument___lon);
     
       instrument___lat:units = "degrees_north";
       instrument___lon:units = "degrees_east";
       time:units = "seconds";
       instrument___rh:_FillValue = -1;
     
       instrument:measurement_platform = "aircraft" ;
       instrument:container_type = 'simple' ;
       instrument:container_members = "instrument___lat instrument___lon instrument___time" ;

       int model ;
     
       int     model___lat(model___lat), model___lon(model___lon);
       int     model___rh(time,model_lat,model_lon);
     
       model___lat:units = "degrees_north";
       model___lon:units = "degrees_east";
       model___rh:_FillValue = -1;
       
       model:measurement_platform = "global circulation model" ;
       model:container_type = 'simple' ;
       model:container_members = "model___lat model___lon model___time" ;
     
     }


NetCDF4 Group
-------------


::

     netcdf foo {    // example netCDF specification in CDL
     
     dimensions:
     time = 5 ;

     variables:
       int     time(time);

       time:units = "seconds";
     
     group instrument {

     dimensions:
       lat = 10, lon = 5 ;
     
     variables:
       int     lat(lat), lon(lon);
       int     rh(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       rh:_FillValue = -1;
     
       :measurement_platform = "aircraft"
     }
     group model {

     dimensions:
       lat = 17, lon = 9 ;
     
     variables:
       int     lat(lat), lon(lon) ;
       int     rh(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       rh:_FillValue = -1;
       
       :measurement_platform = "global circulation model"
     }
     
     }


Degenerate netCDF4 Semantic Group
---------------------------------


::

     netcdf foo {    // example netCDF specification in CDL
     
     dimensions:
     time = 5 ;

     variables:
       int     time(time);

       time:units = "seconds";
     
     group instrument {

     dimensions:
       lat = 10, lon = 5 ;
     
     variables:
       int     lat(lat), lon(lon);
       int     rh(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       rh:_FillValue = -1;
     
       :measurement_platform = "aircraft"
       :container_type = 'simple'
     }
     group model {

     dimensions:
       lat = 17, lon = 9 ;
     
     variables:
       int     lat(lat), lon(lon) ;
       int     rh(time,lat,lon);
     
       lat:units = "degrees_north";
       lon:units = "degrees_east";
       rh:_FillValue = -1;
       
       :measurement_platform = "global circulation model"
       :container_type = 'simple'
     }
     
     }



