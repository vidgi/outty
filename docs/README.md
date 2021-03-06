## Outty Documentation

## Tools Used

* Python/flask + HTML/CSS/JS
* libraries: anime.js bootstrap, jinja
* apis: trail-api, openweather, google maps
* data base: flask-sqlalchemy
* testing: flask-test
* deployment: Heroku, Docker, Github-Secrets, Github-Actions
* See requirements.txt for more details on requirements

### Running the app locally

#### The app is containerized with docker and will require:

* Install docker: https://docs.docker.com/docker-for-mac/install/

* a file called config.py in the venv directory is necessary for managing api keys. It contains the necessary api keys:

    - trail_api_key = "XXXXXXXXXXXXXXXXXXXX" # trail api: https://rapidapi.com/trailapi/api/trailapi

    - geo_encode_key = "XXXXXXXXXXXXXXXXXXXX"  # geo encoding: (google maps geocoding)

    - weather_api_key = "XXXXXXXXXXXXXXXXXXXX" # OpenWeather api

    - map_api_key = "XXXXXXXXXXXXXXXXXXXX"  # Google Maps api

* collaborator access to notion page contains keys in 'notes page'

#### Run app through command line
* ``` cd venv ```

* ``` docker build -t flask-heroku:latest . ```

* ``` docker run -d -p 5000:5000 flask-heroku ```

* See Dockerfile for necessary configuration

* Potentially helpful link: https://medium.com/@ksashok containerise-your-python-flask-using-docker-and-deploy-it-onto-heroku-a0b48d025e43

## Unit Tests:

* Automated unit tests are in test.py. To execude them navigate to /venv and run

* ``` python test.py ```

* Unit tests make use of flask_testing module

## User Tests:
### Create new user
    Use case name
	    New user creation
    Description
        A test to ensure that user is able to create a new user
    Pre-condition
        User is able to access site
        User is able to navigate to signup page
        User is able to enter information into signup page
    Test steps
        User navigates to Outty
        User accesses signup page and enters all the necessary information
        User selects signup
    Expected result
        User is redirected to dashboard page
        When user reviews their profile, they will see all the information they entered while signing up
            When user logs out and logs back in, they will be able to enter the  credentials they used when signing up
        Actual Result
            Same as expected
        Status (Pass/Fail)
            Pass
        Notes
            N/A
        Post-conditions
            User is logged into site and user provided information is stored

### Sign in existing user
	Use case name
        Existing User Sign In
    Description
        A test to ensure that username password combinations are saved correctly when signing up and logging in effectively searches the db and reroutes to user-specific dashboard
    Pre-conditions
        User has signed up
    Test steps
        User logs in and goes to dashboard, check if parameters match
        Go to profile, check if parameters match
        Go to settings, check if parameters match
    Expected result
        Parameters match across pages
    Actual result
    Same as expected results
    Status (Pass/Fail)
        Pass
    Notes
        N/A
    Post-conditions
    Correct parameters should be passable into recommendation functions and update settings functions

### Get recommendation for user
    Use case name
        Recommendation correctness
    Description
        A test to ensure that correct recommendations are provided to the user
    Pre-conditions
        User sign up is functional
    Test steps
    User signs up (provides activity preferences)
    Expected result
        User is navigated to their dashboard (profile?)
        A set of recommendations is displayed in UI
        That set of recommendations includes only the activities that the user selected as their activity preferences
    Actual result
    Same as expected results
    Status (Pass/Fail)
        Pass
    Notes
        N/A
    Post-conditions
        Backend recommendation functions have provided the user with correct UI display and user is able to explore options from there


### Correct user parameters carried across pages
    Use case name
        Correct user parameters maintained across pages
    Description
        A test to ensure that parameters are maintained across pages
    Pre-conditions
        User is logged in and has parameters set
    Test steps
        User logs in and goes to dashboard, check if parameters match
        Go to profile, check if parameters match
        Go to settings, check if parameters match
    Expected result
        Parameters match across pages
    Actual result
    Same as expected results
    Status (Pass/Fail)
        Pass
    Notes
        N/A
    Post-conditions
        Correct parameters should be passable into recommendation functions and update settings functions
