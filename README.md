FCIPAddressGeocoder
===================

iOS Geocoder for **geocode device IP Address location using [FreeGeoIP](https://github.com/fiorix/freegeoip) service** and a block-based syntax.

##Requirements & Dependecies
- iOS >= 5.0
- ARC enabled
- CoreLocation Framework

##Installation

####CocoaPods:
`pod 'FCIPAddressGeocoder'`

####Manual install:
Copy `FCIPAddressGeocoder.h` and `FCIPAddressGeocoder.m` to your project.

##Usage
```objective-c
//if you are running an instance of the FreeGeoIP service on your own server, 
//just set the service url in application:didFinishLaunching, otherwise the default service url will be used
//this method will set the service url for all instances, included the shared one
[FCIPAddressGeocoder setServiceURL:@"http://localhost:8080/"];
```
```objective-c
//you can use the shared instance
FCIPAddressGeocoder *geocoder = [FCIPAddressGeocoder sharedGeocoder];

//or create a new geocoder
FCIPAddressGeocoder *geocoder = [FCIPAddressGeocoder new];

//or create a new geocoder which uses a custom instance of the FreeGeoIP service installed on your own server
FCIPAddressGeocoder *geocoder = [[FCIPAddressGeocoder alloc] initWithServiceURL:"http://localhost:8080/"];
```
```objective-c
//IP Address geocoding (geocoding results are cached for 1 minute)
[geocoder geocode:^(BOOL success) {

    if(success)
    {
        //you can access the location info-dictionary containing all informations using 'geocoder.locationInfo'
        //you can access the location using 'geocoder.location'
        //you can access the location city using 'geocoder.locationCity' (it could be nil)
        //you can access the location country using 'geocoder.locationCountry'
        //you can access the location country-code using 'geocoder.locationCountryCode'
    }
    else {
        //you can debug what's going wrong using: 'geocoder.error'
    }
}];
```
```objective-c
//check if geocoding
[geocoder isGeocoding]; //returns YES or NO
```
```objective-c
//cancel geocoding
[geocoder cancelGeocode];
```

Enjoy :)

