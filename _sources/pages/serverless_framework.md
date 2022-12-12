
## Serverless Framework

### Installing the Serverless framework cli
Go over to https://www.serverless.com/framework/docs/getting-started
Run this command: 
`npm install -g serverless@2.72.3`

verify your version by running: `sls --version` and you should see this line in the console: `Framework Core: 2.72.3`

#### Creating our first app 
We are going to use the serverless framework cli to generate our app. run this command:<br> `sls`<br>
We are going to select this template: `AWS - Python - Flask API with DynamoDB`.<br>
Follow the steps in the cli:
* What do you want to make? AWS - Python - Flask API with DynamoDB
* What do you want to call this project? `please select a short name. e.g my-app`
* What org do you want to add this service to? `[Skip]`

[//]: # (* What application do you want to add this to? Create a new app if you logged in)
* No AWS credentials found, what credentials do you want to use?  `[Skip]` We can skip this step since we are going to work locally.

cd into your project. You will see these files in your project:
* `serverless.yml`
* `package.json`
* `requirements.txt`
* `app.py`

Let's go over the `serverless.yml` file.

## Edit your serverless function definition

Change this:
```yml
functions:
  api:
    handler: wsgi_handler.handler
    events:
      - http:
          path: /
          method: ANY
      - http:
          path: /{proxy+}
          method: ANY
```

To this:

```yml
functions:
  api:
    handler: wsgi_handler.handler
    package:
      exclude:
        - ./**
      include:
        - ./app.py
    events:
      - http:
          path: /
          method: ANY
      - http:
          path: /{proxy+}
          method: ANY
```

It will reduce the size of your lambda to include only the required components.