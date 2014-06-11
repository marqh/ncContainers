Simple Container
================

This is an example of the degenerate case, where a group in netCDF4 is equivalent to a `simple` semantic container, which is equivalent to a NetCDF3 `simple` container.

All four of these examples are semantically identical and software should be able to transform data files between the encoding options at will.


Semantic Container NetCDF3 Classic
----------------------------------

::

     netcdf foo {    // example netCDF specification in CDL
     
     dimensions:
          instrument___lat = 10 ;
	  instrument___lon = 5 ;
          model___lat = 17 ;
	  model___lon = 9 ;
	  time = 5 ;
     variables:
       float time(time) ;
         time:units = "seconds";
	        
       int instrument ;
         instrument:measurement_platform = "aircraft" ;
         instrument:container_type = 'simple' ;
         instrument:container_members = "instrument___lat instrument___lon instrument___time" ;
       
       float instrument___lon(instrument___lon);
         instrument___lon:units = "degrees_east";
	 
       float instrument___lat(instrument___lat) ;
         instrument___lat:units = "degrees_north";
	 
       float instrument___rh(time,instrument___lat,instrument___lon);
         instrument___rh:long_name = "relative humidity of air"
         instrument___rh:_FillValue = -1;
     

       int model ;
         model:measurement_platform = "global circulation model" ;
         model:container_type = 'simple' ;
         model:container_members = "model___lat model___lon model___time" ;
            
       float model___lat(model___lat) ;
         model___lat:units = "degrees_north";
       
       float model___lon(model___lon) ;
         model___lon:units = "degrees_east";
       
       float model___rh(time,model_lat,model_lon);
         model___rh:_FillValue = -1;
	 model___rh:long_name = "relative humidity of air"
       
     
     }


NetCDF4 Group
-------------


::

     netcdf foo {    // example netCDF specification in CDL
     
     dimensions:
     time = 5 ;

     variables:
       float time(time);
         time:units = "seconds";
     
     group instrument {

     dimensions:
       lat = 10, lon = 5 ;
     
     variables:
       float lat(lat) ;
         lat:units = "degrees_north";
       
       float lon(lon) ;
         lon:units = "degrees_east";
       
       float rh(time,lat,lon);
         rh:_FillValue = -1;
         rh:long_name = "relative humidity of air"
     
       :measurement_platform = "aircraft"
     }
     group model {

     dimensions:
       lat = 17, lon = 9 ;
     
     variables:
       float lat(lat) ;
         lat:units = "degrees_north";
       
       float lon(lon) ;
         lon:units = "degrees_east";
       
       float rh(time,lat,lon);
         rh:_FillValue = -1;
         rh:long_name = "relative humidity of air"
       
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
       float     time(time);
         time:units = "seconds";
     
     group instrument {

     dimensions:
       lat = 10, lon = 5 ;
     
     variables:
       float lat(lat) ;
         lat:units = "degrees_north";
       
       float lon(lon) ;
         lon:units = "degrees_east";
       
       float rh(time,lat,lon) ;
         rh:_FillValue = -1;
         rh:long_name = "relative humidity of air"
     
       :measurement_platform = "aircraft"
       :container_type = 'simple'
     }
     group model {

     dimensions:
       lat = 17, lon = 9 ;
     
     variables:
       float lat(lat) ;
         lat:units = "degrees_north";
       
       float lon(lon) ;
         lon:units = "degrees_east";
       
       float rh(time,lat,lon);
         rh:_FillValue = -1;
         rh:long_name = "relative humidity of air"
       
       :measurement_platform = "global circulation model"
       :container_type = 'simple'
     }
     
     }



