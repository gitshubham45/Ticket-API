Process for running ang testing the APIs.

1.) Download or clone the repository to local host.
2.) Open terminal go to the folder of cloned or downloaded repository.
3.) Run command "npm install" , to install all the required dependencies.
4.) Create a new directory named ".env".
5.) Add the following environment variables.
    i) MONGODB_URI 
    ii) JWT_SECRET 
    iii) PORT 

6.) After adding the above environment variables run command "nodemon index.js".
7.) Go to Postman for testing APIs.
8.) Testing APIs

    i.) First create a POST request to REGISTER user with url `http://localhost:${port}/user/register' (enter your port number by replacing ${port} ) and provide raw data in body in JSON format.

    url e.g -`http://localhost:3000/user/register`

    e.g -
        {
            "username" : "ram@gmail.com",
            "password" : "12345"
        }
    if registration is successful then you will get a message -{
        "message" : "Registration successful",
    }

    ii) After registration is successful Create another POST request for LOGIN with url
    `http://localhost:${port}/user/register' (enter your port number by replacing ${port} ) and 
    provide same details at the time of registration.

    url e.g - `http://localhost:3000/user/login`.

    e.g -
        {
            "username" : "ram@gmail.com",
            "password" : "12345"
        }
    
    After login you will get a message "login successful" along with a token . Copy that token and go to authorization tab and select "Bearer Token" and put the token string without quotes and make it global variable.

    e.g-

    {
        "message": "Login successful",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InJhbUBnbWFpbC5jb20iLCJpYXQiOjE2ODQ2NDk3MjIsImV4cCI6MTY4NDczNjEyMn0.6GsGmtUnXLT2Eduh-zsKOmXHiEoajvEGpvQRln4i_F8"
    }

    iii) Cerate another POST request for generating tickets with url `http://localhost:${port}/tickets' (enter your port number by replacing ${port} ). make sure to check wether the same "Bearer Token" is present in authorization or not as it was received after login.

    url e.g - `http://localhost:3000/tickets'

    Provide number of tickets you want to generate as -
    {
        "num_tickets" : 10
    }

    after sending the POST request if the request is successful then you will get a ticketID as- 
    {
        "ticketID": "6469a745721b90b8752480e2",
    }

    copy this id to paste in the next request as params.
    
    iv) Create a GET request for fetching all tickets with url `http://localhost:${port}/:id' (enter your port number by replacing ${port} an :id coped id from previous request).
    Make sure to check wether the same "Bearer Token" is present in authorization or not as it was received after login.

    url eg. -> `http://localhost:3000/6469a745721b90b8752480e2' 

    you can also pass query parameters as "page" and "limit"

    url e.g. -> `http://localhost:3000/6469a745721b90b8752480e2?page=1&limit=5' 
    it will return first 5 tickets on the first page.

9.) You can verify the results





