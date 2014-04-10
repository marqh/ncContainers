Uncertainty
===========

NetCDF3 Encoding
----------------

::

  netcdf ssl {
  
  dimensions:
    lat = 180 ;
    lon = 360 ;
    time = 11 ;
    time_bnds = 2 ;
  
  variables:
    sst_collection ;
        sst_collection:container_type = " http://www.uncertml.org/statistics/statistics-collection"
        sst_collection:container_members = "total_uncert uncorr_sd synopcorr_sd system_err best_estimate" ;
        sst_collection:base_phenomenon = "sea_surface_temperature" ;
	sst_collection:base_units = 'K' ;

    total_uncert ;
        total_uncert:container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        total_uncert:sample_variable = "time" ;
        total_uncert:container_members = "total_uncert_data" ;
        total_uncert:comment = " total estimated error distribution (non-systematic) ;

    uncorr_sd ;
        uncorr_sd:container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        uncorr_sd:sample_variable = "time" ;
        uncorr_sd:container_members = "uncorr_sd_data" ;
        uncorr_sd:comment = "uncorrelated effects (instrument noise, sampling uncertainty)" ;

    synopcorr_sd ;
        synopcorr_sd:container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        synopcorr_sd:sample_variable = "time" ;
        synopcorr_sd:container_members = "synopcorr_sd_data" ;
        synopcorr_sd:comment = "synoptically-correlated effects (due to retrieval errors associated with large weather systems)" ;

    system_err ;
        system_err:container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        system_err:sample_variable = "time" ;
        system_err:container_members = "system_err_data" ;
        system_err:comment = "Uncertain systematic errors (i.e. unknown biases due to the inversion process)" ;

    best_estimate ;
        best_estimate:container_type = "http://www.uncertml.org/statistics/mean" ;
        best_estimate:sample_variable = "time" ;
        best_estimate:container_members = "best_estimate_data" ;
        best_estimate:comment = "best estimate" ;


    total_uncert_data(time, lat, lon) ;

    uncorr_sd_data(time, lat, lon)  ;

    synopcorr_sd_data(time, lat, lon)  ;

    system_err_data(time, lat, lon)  ;

    best_estimate_data(time, lat, lon)  ;

    lat(lat) ;

    lon(lon) ;

    time(time) ;
    
    }


NetCDF4 Encoding
----------------

::

  netcdf ssl {
  
  dimensions:
    lat = 180 ;
    lon = 360 ;
    time = 11 ;
    time_bnds = 2 ;
  
  group sst_stats {
  	
	variables:
	
        lat(lat) ;
        lon(lon) ;
        time(time) ;

        :container_type = " http://www.uncertml.org/statistics/statistics-collection"
        :base_phenomenon = "sea_surface_temperature" ;
	:base_units = 'K' ;

    group total_uncert {
  	
	variables:
	
        total_uncert_data(time, lat, lon) ;

        :container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        :sample_variable = "time" ;
        :comment = " total estimated error distribution (non-systematic) ;
	
	}

    group uncorr_sd {
    
	variables:
	
	uncorr_sd_data(time, lat, lon)  ;
	
        container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        sample_variable = "time" ;
        comment = "uncorrelated effects (instrument noise, sampling uncertainty)" ;
	
	}

    group synopcorr_sd {
    	
	variables:
	
	synopcorr_sd_data(time, lat, lon)  ;
	
        :container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        :sample_variable = "time" ;
        :comment = "synoptically-correlated effects (due to retrieval errors associated with large weather systems)" ;
	
	}

    group system_err {
    	
	variables:
	
	system_err_data(time, lat, lon)  ;
	
        :container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        :sample_variable = "time" ;
        :comment = "Uncertain systematic errors (i.e. unknown biases due to the inversion process)" ;
	
	}

    group best_estimate {
    	
	variables:
	
	best_estimate_data(time, lat, lon)  ;
	
        :container_type = "http://www.uncertml.org/statistics/mean" ;
        :sample_variable = "time" ;
        :comment = "best estimate" ;
	
	}
    }
  
  }
