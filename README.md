# distance-between-zipcode in KM

    function distanceBetweenzipcodes($zipcode, $zipcode2){
        try{
            $url ="https://maps.googleapis.com/maps/api/distancematrix/json?origins=".$zipcode."&destinations=".$zipcode2."&mode=car&sensor=false&key=";
            $details=file_get_contents($url);
            $result = json_decode($details,true);
            $distance = $result['rows'][0]['elements'][0]['distance']['value'] ?? 0;
            if($distance==0){
                return 0;
            }
            return  $distance/1000;
        }
        catch(\Exception $e){
            return 0;
        }
    }
    
    echo distanceBetweenzipcodes(127021,127031);
    
    #calculate distance between two zipcode. please pass google map api key to this method
