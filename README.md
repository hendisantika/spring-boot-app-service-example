# spring-boot-app-service-example

![travis status](https://travis-ci.org/hendisantika/spring-boot-app-service-example.svg?branch=master)

Source code reference for Java Magazine Article (coming soon)

fake rest service on base of:

* spring boot
* swagger
* oAuth2  + JWT
* docker


important commands

    $ ./gradlew bootRun
    $ ./gradlew buildDocker
    $ docker run -p 8080:8080 -t hendisantika/spring-boot-app-service-example
    
use the api:


    curl -X POST -H "Content-Type: application/json" http://localhost:8080/register -d 
       '{ 
           "mail": "uzumaki_naruto@konohagakure.co.jp",
           "password": "rasengan",
           "lastName": "naruto",
           "name": "Uzumaki Naruto",
           "firstName": "uzumaki",
           "address": "Konohagakure"
        }'
        
    curl -vu aClient:aSecret -X POST 'http://localhost:8080/oauth/token?username=uzumaki_naruto@konohagakure.co.jp&password=x&grant_type=password'
    
this should return something like

    { "access_token":"eyJhbGci...YBPFpao",
       "token_type":"bearer",
       "refresh_token":"eyJhbGci...Rz4clI",
       "expires_in":43199,
       "scope":"read write",
       "jti":"6e0978db-2725-47c4-905b-c6c6e84acb31"
    }

which you can use to retrieve data by    
        
    curl -i -H "Authorization: Bearer eyJhbGci...YBPFpao" http://localhost:8080/user    

of course using the swagger api is easier http://localhost:8080/swagger-ui.html
