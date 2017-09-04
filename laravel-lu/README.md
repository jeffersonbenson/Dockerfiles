# laravel-lu
[![](https://images.microbadger.com/badges/image/jeffersonbenson/laravel-lu.svg)](https://microbadger.com/images/jeffersonbenson/laravel-lu "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/jeffersonbenson/laravel-lu.svg)](https://microbadger.com/images/jeffersonbenson/laravel-lu "Get your own version badge on microbadger.com")
LU's latest and greatest dev environment! Now with 100% more Laravel!

     docker run -it -v /path/to/project:/var/www/laravel -p 80:80 laravel-lu

## Notes
While this mostly just serves as a backup location for this Dockerfile, there are a few things of note:

1. Both the Oracle instantclient and instantclient-sdk are required for proper OCI installation. They are not in this repo due to copyright concerns, but both can be found [here.](http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html)
2. This container assumes you already have an existing Laravel project. Documentation for setting up a Laravel project can be founde [here.](https://laravel.com/docs/5.4)
3. This file is very WIP as environment configurations shift and change.
4. Pull requests are always welcome.
