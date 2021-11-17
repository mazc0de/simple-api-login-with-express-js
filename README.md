# Simple REST API Login with Authentication NodeJS and ExpressJS

In this project i'm creating a login authentication using Node JS but not using a third-party library, the access token in this project is stored in a variable in the project.
And also merge the previous projects in [this repository][ch3] and [this repository][ch4], where this time i'm use a view engine called handlebars to display the user interface.

## Features

- User can login with headers authorization
- Middleware can handle not found page and when server error

## Ingredients

- Node JS
- Express JS
- Handlebars
- HTML
- CSS
- Javascript
- Bootstrap
- Animate On Scroll JS

## Installation

In this project i'm recommend installing node js and npm with the latest versions

Install the dependencies and devDependencies and start the server.

```sh
$ git clone https://github.com/mazc0de/simple-api-login-with-express-js.git
$ cd simple-api-login-with-express-js
$ npm install
$ npm install -g nodemon
$ npm run dev
```

Access the landing page

```sh
$ npm run dev
open in browser http://localhost:1337/
```

Access the rock paper scissors mini games

```sh
$ npm run dev
open in browser http://localhost:1337/game
```

## API's documentation

### API Endpoints

```
GET http://localhost:1337/api/me
```

```
POST http://localhost:1337/api/login
```

```
404 : http://localhost:1337/not-found
```

```
500 : http://localhost:1337/server-error
```

## API Response

### GET

1. when accessing this endpoints without headers authorization will get response

```
GET http://localhost:1337/api/me

{
    "status": 401,
    "data": {
        "message": "Unauthorized, you no have access!"
    }
}
```

2. when accessing this endpoints with wrong headers authorization will get response

```
GET http://localhost:1337/api/me

{
    "status": 401,
    "data": {
        "message": "Unauthorized, please input key correctly!"
    }
}
```

3. when accessing this endpoints with headers authorization default where stored in app ('rahasia') will get response

```
GET http://localhost:1337/api/me

{
    "status": 401,
    "data": {
        "message": "Unauthorized, you must login first!"
    }
}
```

because user not yet login and don't have access token yet

4. when accessing this endpoints with correctly headers authorization will get response

```
GET http://localhost:1337/api/me

{
    "status": 200,
    "data": {
        "userLogin": [
            {
                "id": 1,
                "username": "daffa",
                "password": "daffa123",
                "firsName": "Daffa",
                "lastName": "Hanifisyafiq",
                "email": "daffa@gmail.com",
                "ages": 21,
                "address": {
                    "houseNumber": 69,
                    "street": "Sudirman St.",
                    "subDistrict": "Petarukan",
                    "regency": "Pemalang",
                    "province": "Central Java",
                    "postalCode": 52362,
                    "country": "Indonesia"
                }
            }
        ]
    }
}
```

5. when accessing this endpoint you will logout and reset token and authorization

```
GET http://localhost:1337/api/logout

{
    "status": 201,
    "data": {
        "message": "successfully logout!"
    }
}
```

but if you not yet logged in, you will get response like this

```
{
    "status": "FAIL",
    "data": {
        "message": "you are not logged in!"
    }
}
```

### POST

Dummy user data :

```
username : daffa
password : daffa123
```

1. when accessing this endpoint with wrong username and password will get response

```
POST http://localhost:1337/api/login

{
    "status": 401,
    "data": {
        "message": "Unauthorized, username or password is wrong"
    }
}
```

2. when accessing this endpoint with correctly username and password will get response

```
POST http://localhost:1337/api/login

{
    "status": 201,
    "data": {
        "message": "login success",
        "username": "daffa",
        "accessToken": "daffa-rahasia"
    }
}
```

3. when accessing this endpoint but you have logged in will get response

```
POST http://localhost:1337/api/login

{
    "status": 200,
    "data": {
        "message": "you have login"
    }
}
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # "These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax"
[ch3]: https://github.com/mazc0de/traditional-game-landing-page
[ch4]: https://github.com/mazc0de/rock-paper-scrissors-mini-games
