# guest-service-for-OAuth2
run this in conjunction of spring-security-OAuth2-authentication-and-authorization

## Inorder to test this service using httpie , do following :

->   Install httpie  -  https://httpie.org/doc#installation
->   Issue following commands:  

C:\Users\DELL\AppData\Roaming\Python\Python37\Scripts>http --form POST localhost
:8100/oauth/token
HTTP/1.1 401
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Content-Type: application/json;charset=UTF-8
Date: Sun, 16 Dec 2018 07:28:46 GMT
Expires: 0
Pragma: no-cache
Transfer-Encoding: chunked
WWW-Authenticate: Basic realm="oauth2/client"
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

{
    "error": "Unauthorized",
    "message": "Unauthorized",
    "path": "/oauth/token",
    "status": 401,
    "timestamp": "2018-12-16T07:28:45.841+0000"
}


C:\Users\DELL\AppData\Roaming\Python\Python37\Scripts>http --form POST localhost
:8100/oauth/token Authorization:"Basic Z3Vlc3RfYXBwOnNlY3JldA=="
HTTP/1.1 400
Cache-Control: no-store
Connection: close
Content-Type: application/json;charset=UTF-8
Date: Sun, 16 Dec 2018 07:29:41 GMT
Pragma: no-cache
Transfer-Encoding: chunked
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

{
    "error": "invalid_request",
    "error_description": "Missing grant type"
}


C:\Users\DELL\AppData\Roaming\Python\Python37\Scripts>http --form POST localhost
:8100/oauth/token Authorization:"Basic Z3Vlc3RfYXBwOnNlY3JldA==" client_type=cli
ent_credentials
HTTP/1.1 400
Cache-Control: no-store
Connection: close
Content-Type: application/json;charset=UTF-8
Date: Sun, 16 Dec 2018 07:30:48 GMT
Pragma: no-cache
Transfer-Encoding: chunked
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

{
    "error": "invalid_request",
    "error_description": "Missing grant type"
}


C:\Users\DELL\AppData\Roaming\Python\Python37\Scripts>http --form POST localhost
:8100/oauth/token Authorization:"Basic Z3Vlc3RfYXBwOnNlY3JldA==" grant_type=clie
nt_credentials
HTTP/1.1 200
Cache-Control: no-store
Content-Type: application/json;charset=UTF-8
Date: Sun, 16 Dec 2018 07:31:05 GMT
Pragma: no-cache
Transfer-Encoding: chunked
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

{
    "access_token": "c095c5ae-5f79-40cd-9b35-23ac95648960",
    "expires_in": 43199,
    "scope": "READ_ALL_GUSETS WRITE_GUESTS UPDATE_GUEST",
    "token_type": "bearer"
}


C:\Users\DELL\AppData\Roaming\Python\Python37\Scripts>http --form localhost:8100
/oauth/check_token Authorization:"Bearer c095c5ae-5f79-40cd-9b35-23ac95648960" t
oken=c095c5ae-5f79-40cd-9b35-23ac95648960
HTTP/1.1 200
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Content-Type: application/json;charset=UTF-8
Date: Sun, 16 Dec 2018 07:33:19 GMT
Expires: 0
Pragma: no-cache
Transfer-Encoding: chunked
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

{
    "active": true,
    "authorities": [
        "ROLE_GUESTS_AUTHORIZED_CLIENT"
    ],
    "client_id": "guest_app",
    "exp": 1544988665,
    "scope": [
        "READ_ALL_GUSETS",
        "WRITE_GUESTS",
        "UPDATE_GUEST"
    ]
}


C:\Users\DELL\AppData\Roaming\Python\Python37\Scripts>http --form POST localhost
:8100/oauth/token Authorization:"Basic YXBpX2F1ZGl0OnNlY3JldA==" grant_type=clie
nt_credentials
HTTP/1.1 200
Cache-Control: no-store
Content-Type: application/json;charset=UTF-8
Date: Sun, 16 Dec 2018 07:36:00 GMT
Pragma: no-cache
Transfer-Encoding: chunked
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

{
    "access_token": "b97259a5-12e9-4f72-85d8-e6b6833c57fa",
    "expires_in": 43199,
    "scope": "READ_ALL_GUESTS",
    "token_type": "bearer"
}


C:\Users\DELL\AppData\Roaming\Python\Python37\Scripts>http --form localhost:8100
/oauth/check_token Authorization:"Bearer b97259a5-12e9-4f72-85d8-e6b6833c57fa" t
oken=b97259a5-12e9-4f72-85d8-e6b6833c57fa
HTTP/1.1 200
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Content-Type: application/json;charset=UTF-8
Date: Sun, 16 Dec 2018 07:36:37 GMT
Expires: 0
Pragma: no-cache
Transfer-Encoding: chunked
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

{
    "active": true,
    "authorities": [
        "ROLE_GUESTS_AUTHORIZED_CLIENT"
    ],
    "client_id": "api_audit",
    "exp": 1544988960,
    "scope": [
        "READ_ALL_GUESTS"
    ]
}


