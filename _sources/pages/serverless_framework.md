
## Serverless Framework

### Installing the Serverless framework cli
Go over to https://www.serverless.com/framework/docs/getting-started
Run this command: 
`npm install -g serverless@2.72.3`

verify your version by running: `sls --version` and you should see this line in the console: `Framework Core: 2.72.3`

#### Optional: create your serverless framework account
We will not need this in our workshop but if you want to deploy to the cloud it will give you some more added value. <br>
Go over to https://app.serverless.com/ and create your free account.<br>
if you've created your serverless framework account, let's login through the cli `sls login`

#### Creating our first app 
Running the cli like this will create our templated app: `sls`. We are going to select this template: `AWS - Python - Flask API with DynamoDB`.<br>
Follow the steps in the cli:
* What do you want to make? AWS - Python - Flask API with DynamoDB
* What do you want to call this project? (aws-python-flask-dynamodb-api-project)
* What org do you want to add this service to? if you've created your serverless account you could add it here or optionally skip this step
* What application do you want to add this to? Create a new app if you logged in
* No AWS credentials found, what credentials do you want to use? We can skip this step since we are going to work locally.

cd into your project. You will see these files in your project:
* serverless.yml
* package.json
* requirements.txt
* app.py

Let's go over the `serverless.yml` file.