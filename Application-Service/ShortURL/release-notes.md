## Application Service > ShortURL > Release Notes

### January 31, 2023
* Fixed an issue where, when characters outside the ASCII(7) encoding range such as Korean are contained in the original URL, redirection of shortened URLs does not work properly.
    * When accessing the original URL through the shortened URL created, the original URL is converted into an ASCII (7) string and added to the Location header.
    * In this case, the character + is used without any additional encoding.
        * For example, `https://nhn.com?query=안+녕` is converted to `https://nhn.com?query=%EC%95%88+%EB%85%95` and the character `+ ` is not encoded separately as `%2B`.

### October 25, 2022

#### Feature Updates
* Changed so that the status value cannot be used when searching for a shortUrl.
* Changed so that the text search condition is limited to the backHalf of the shortUrl when searching for a shortUrl.

### June 30, 2022

#### Feature Updates
* Changed the domain name of the API endpoint from `api-shorturl.cloud.toast.com` to `api-shorturl.nhncloudservice.com`.
* Added the QR code download function.
    * You can download a QR code image by clicking the QR code of a generated shortened URL.

### March 29, 2022

#### Feature Updates
* Changed so that the queryParameter feature can be enabled or disabled on a per-project basis.

### November 23, 2021

#### Feature Updates
* Switched from beta service to official service.
* Improved certificate renewal feature
    * Expired certificates are displayed as expired status.
    * You can use the Edit button to renew the certificate to a certificate with the same common name (CN).

#### Bug Fixes
* Fixed an issue where expiration date is not set correctly when generating shortUrl through API.

### September 28, 2021

#### Feature Updates
* Added a feature to append a query parameter after ShortUrl.
    * For example, if `nh.nu/abc` is linked to `www.coupang.com/vp/products/1821016708`, `nh.nu/abc?param=param` is linked to `www.coupang.com/vp/products/1821016708?param=param`.

#### Bug Fixes
* Fixed an issue where the status display color in the certificate list does not match the actual status intermittently.

### August 24, 2021

#### Bug fixes
* Fixed an issue where, when you delete an affiliated URL of a campaign, all affiliated URLs of the campaign are deleted.

### July 27, 2021

#### Feature Updates
* You can check each event in Cloud Trail.

#### Bug Fixes
* Fixed an issue where a project that was supposed to be unavailable could be selected when specifying the target to share the domain and certificate.

### June 29, 2021

#### Feature Updates
* When registering a certificate for an already existing domain, the name of the project with the registered certificate will be provided.
* The recently registered shortUrl is at the top of the list.

#### Bug Fixes
* Fixed an issue where the full URL can be modified in the shortened URL edit screen.

### May 25, 2021

#### Feature Updates
* Added a [Console] page feature
    * Added the page feature to View > URL screen.

### April 27, 2021

#### New Service Release
* ShortURL allows you to share your website link with a shorter character length in a wide variety of environments where writing space is limited.
* RESTful API is provided to users for easy link with apps.
