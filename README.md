# Web App run on Heroku Server, build with nodes.js/.json/.html 
# Exepdia Bookings
This is an initial version of a website for travel booking developed in JS, JSON, HTML, Heroku Server, Git

- Website is run on Heroku Server
- In order to run this code you need to have:
  1. GIT installed
  2. Heroku terminal commands installed
  
 - To do changes on this version you need to work on the server.js file, package.json
 
# Deploying on the Cloud with Heroku

To deploy the application on the cloud you can use Heroku, a Java-capable, Polyglot Platform-as-a-Service (PaaS) provider. For this example we will upload the code via git to Heroku. This method supports "Continuous Delivery" by making incremental changes very easy to deploy. Every time new code is received by Heroku (through a git push), the Maven build will be run and the new version deployed. Follow these steps to deploy your copy of this app on Heroku:

1) Signup for a Heroku account. You will be able to deploy and run this application for free on one dyno.

2) Verify your Heroku account. (Required to use the free tier of the MongoLab add-on.)

3) Install the Heroku Toolbelt.

4) Login to Heroku from the command line:

    heroku login
This will also help you setup your SSH key and associate it with your Heroku account. The SSH key will be used for authenticating git pushes (uploads).

5) Provision a new app on Heroku (using the cedar stack) with the MongoLab add-on (run this command in the root of your project):

    heroku create --stack cedar --addons mongolab
The git remote endpoint for the newly created app will be named "heroku" and will be automatically added to your git configuration.

6) Using git, upload your application to Heroku:

    git push heroku master
You can also do this from within your IDE. This will copy the source files, Maven build descriptor, and the Procfile to Heroku. Heroku will then run the Maven build on the project, deploy the app onto a dyno, and launch the web process defined in the Procfile. The Procfile is just a simple way to map process names to commands. Here is the Procfile for this project:

    web:    java -cp target/classes:target/dependency/* com.jamesward.jaxrsbars.BarServer
Notice that the launch command on Heroku is the same as the one that you used to start BarServer locally.

Once the git push is complete you should be able to open your app in the browser using either the URL from the git push output or by running:

    heroku open
7) By default caching and 304 handling was turned off for local development. Turn that on by setting the FILE_CACHE_ENABLED environment variable on Heroku:

    heroku config:add FILE_CACHE_ENABLED=true
You can see a full list of environment variables for your application (including MONGOLAB_URI that was set by the MongoLab add-on) by running:

    heroku config
Congrats! Your application is now running on the cloud!
