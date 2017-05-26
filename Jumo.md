## 1. How would you test that the platform is functioning correctly?
Behavioral API testing: Ensure that the API delivers expected behavior and handles unexpected behavior properly. For example, test that the response Data is structured correctly(JSON) and similarly handling of invalid argument values.

Solution-oriented API testing: Ensure that the API as a whole supports the intended use cases that it was designed to solve.

## 2. What kinds of tests would you want to run? 
Functional testing - test that the API is functional and behaves as intended.

Security testing - test what type of authentication is required and whether sensitive data is encrypted.

Negative testing - test what happens if I send incorrect data or invalid requests to the API.

Performance testing - test whether or not the response time to and from the API are within reasonable timings or whether it is high.

Load testing - test how the API functions under irregular application load.

Component testing - test how the components behave in the absense of each other and that they deal with error handling. For example, how does the API behave when it cannot talk to the database, or when it cannot talk to the integration gateway. Does it return humanly accepatable responses in those situations?

## 3. Outline your test scenarios (in realation to the above)
Functional testing
Test the return of a value based on inputs - define a set of inputs and authenticate the results. For example add(int1, int2) then validate the known results.

Security testing 
In the case that it is a private API, what happense if is send a request with unauthorised signatures or encryption?

Negative testing
Test that the API can gracefully handle invalid input or unexpected behaviour like corrupted JSON or bad parameters.

Performance testing
Test then when making requests to and from the API, investigate the response timings with tools like Zipkin or Google Dapper, for bottlenecks or latency.

Load testing
Test that you can deal with 3 times the traffic going through the API and how it handles the load (assuming next year the clients using the API will grow by 3 times that of the previous year)

Component testing
Test that when sending a request to or from the API that if it takes too long to get a response, it re-tries x amount of times before regarding it as a failed message.

## 4. What tools would you use to do these tests and why?
There are many many tools on the market I could use for testing, some of them I would use:

 - a straight Unit testing framework PyUnit, JUnit, NUnit etc... (I like coding, so quite often use this.)
 - Postman (REST APIs)
 - SoapUI (SOAP services and easy to use)
 - Curl (I like using command line interfaces, so often use this.)
 - Apache Jmeter (Can double as a load testing tool)
 
 Some other tools for mocking or data generation I would use:
- Faker for Python or Ruby (language dependent)
- DBUnit
- TestNG

## 5. What opportunities do you see for automation?
the API interacts with a database and has the ability to create, modify and delete data therfor I'll mock the interaction with the database, so tests can be more consistant, offer repeatability and have less chance of tests failing due to corrupted data.

Could use a tool like vREST for automation, it can do all sorts of things like test case generator, response validatiom, JIRA integration, bulk operation and continuous integration etc...

## 6. What tools would you use for this automation and why?
I would use continuous integration / delivery tool like Jenkins, Travis, Circle CI or Team City to automate the testing process.

I would use Githooks the listen for changes in the source code, and if it finds changes, then it kicks of the test.

I would use a code coverage tool, so I can see whether converage is increasing or decreasing.

Lastly I will add some plugins like Allure to my continuous integration for reporting on my test results (if it doesn't already have it out of the box)