Syntax and semantics for HiFi URLS:

    hifi://LOCATION
    hifi://DOMAIN[/LOCATION[/ROTATION]]
where:  
_DOMAIN_ = hostname or ip address of the Domain manager  
_LOCATION_ = _x,y,z_  (decimal points may be replaced with '\_')  
_| LOCATION_ = @username  
_| LOCATION_ = #locationname  
_| LOCATION_ = name  (search for name as either username or locationname)  
_ROTATION_ = w,x,y,z (quaternion rotation of the avatar in global coordinates)  