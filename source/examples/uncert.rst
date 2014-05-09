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
    float sst_collection ;
        sst_collection:container_type = " http://www.uncertml.org/statistics/statistics-collection"
        sst_collection:container_members = "total_uncert uncorr_sd synopcorr_sd system_err best_estimate" ;
        sst_collection:base_phenomenon = "sea_surface_temperature" ;
	sst_collection:base_units = 'K' ;

    float total_uncert ;
        total_uncert:container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        total_uncert:sample_variable = "time" ;
        total_uncert:container_members = "total_uncert_data" ;
        total_uncert:comment = " total estimated error distribution (non-systematic) ;

    float uncorr_sd ;
        uncorr_sd:container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        uncorr_sd:sample_variable = "time" ;
        uncorr_sd:container_members = "uncorr_sd_data" ;
        uncorr_sd:comment = "uncorrelated effects (instrument noise, sampling uncertainty)" ;

    float synopcorr_sd ;
        synopcorr_sd:container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        synopcorr_sd:sample_variable = "time" ;
        synopcorr_sd:container_members = "synopcorr_sd_data" ;
        synopcorr_sd:comment = "synoptically-correlated effects (due to retrieval errors associated with large weather systems)" ;

    float system_err ;
        system_err:container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        system_err:sample_variable = "time" ;
        system_err:container_members = "system_err_data" ;
        system_err:comment = "Uncertain systematic errors (i.e. unknown biases due to the inversion process)" ;

    float best_estimate ;
        best_estimate:container_type = "http://www.uncertml.org/statistics/mean" ;
        best_estimate:sample_variable = "time" ;
        best_estimate:container_members = "best_estimate_data" ;
        best_estimate:comment = "best estimate" ;


    float total_uncert_data(time, lat, lon) ;

    float uncorr_sd_data(time, lat, lon)  ;

    float synopcorr_sd_data(time, lat, lon)  ;

    float system_err_data(time, lat, lon)  ;

    float best_estimate_data(time, lat, lon)  ;

    float lat(lat) ;

    float lon(lon) ;

    float time(time) ;

    float time_bnds(time_bnds)
    
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
	
        float lat(lat) ;
        float lon(lon) ;
        float time(time) ;

        :container_type = " http://www.uncertml.org/statistics/statistics-collection"
        :base_phenomenon = "sea_surface_temperature" ;
	:base_units = 'K' ;

    group total_uncert {
  	
	variables:
	
        float total_uncert_data(time, lat, lon) ;

        :container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        :sample_variable = "time" ;
        :comment = " total estimated error distribution (non-systematic) ;
	
	}

    group uncorr_sd {
    
	variables:
	
	float uncorr_sd_data(time, lat, lon)  ;
	
        container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        sample_variable = "time" ;
        comment = "uncorrelated effects (instrument noise, sampling uncertainty)" ;
	
	}

    group synopcorr_sd {
    	
	variables:
	
	float synopcorr_sd_data(time, lat, lon)  ;
	
        :container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        :sample_variable = "time" ;
        :comment = "synoptically-correlated effects (due to retrieval errors associated with large weather systems)" ;
	
	}

    group system_err {
    	
	variables:
	
	float system_err_data(time, lat, lon)  ;
	
        :container_type = "http://www.uncertml.org/statistics/standard-deviation" ;
        :sample_variable = "time" ;
        :comment = "Uncertain systematic errors (i.e. unknown biases due to the inversion process)" ;
	
	}

    group best_estimate {
    	
	variables:
	
	float best_estimate_data(time, lat, lon)  ;
	
        :container_type = "http://www.uncertml.org/statistics/mean" ;
        :sample_variable = "time" ;
        :comment = "best estimate" ;
	
	}
    }
  
  }
