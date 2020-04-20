# Quickstart

There are a few prerequisites you need to install and configure:

- Install Node.js 6.x or later on your local machine
- Install the Serverless Framework open-source CLI version 1.47.0 or later
- Install kumologica-serverless plugin.

If you already have these prerequisites setup you can skip ahead to Create a new service from a Template.

### Install Dependencies

**Install Node.js and NPM**

- Follow these [installation instructions](https://nodejs.org/en/download/)
- You should be able to run node -v from your command line and get a result like this...

```
$ node -v
vx.x.x
```

You should also be able to run npm -v from your command line and should see...

```
$ npm -v
x.x.x
```

**Install kumologica-serverless plugin**

Run the following command in your terminal

```
serverless plugin install --name kumologica-serverless
```

## Create new kumologica service from a Template

Use the Serverless Framework open-source CLI to create a new Service:

```
sls create --template-url https://github.com/KumologicaHQ/serverless-templates/tree/master/helloworld-api --path helloworld-api
```

<div class="alert alert-info"> 
Kumologica projects can be deployed on different serverless platforms. As a consequence, it is not required to provide a lambda file or specify the `handler` key within your `serverless.yml` file. The plugin `kumologica-serverless` will take care of those details for you.

After lambda file is created by plugin, the npm install is called and all node modules specified in package.json are installed. All modules are deleted at the end of deploy process.

If you are interested, you can always unzip the artefact file within the `.serverless` directory to see the effect of the plugin or see the final version of cloud formation scripts generated.

</div>

## Edit your Flow

Install [Kumologica Designer](https://kumologica.com/download.html) to open and modify your flow.
The default flow handles api call GET /dev/hello and returns hello world. Kumologica designer allows
implementation of any integration flow providing rich set of outbound nodes and additional repository of 
contribution flows.

Kumologica Designer is available for free on Windows or Mac.

## Deploy your flow

Use this command to deploy your service for the first time and after you make changes to your Functions, Events or Resources in serverless.yml and want to deploy all changes within your Service at the same time.

```
sls deploy -v
```

## Test your service

Replace the URL in the following curl command with your returned endpoint URL, which you can find in the sls deploy output, to hit your URL endpoint.

```
$ curl -X POST https://xxxxxxxxxx.execute-api.{your_region}.amazonaws.com/dev/hello
```

## Remove your Service

If at any point you no longer need your Service, you can run the following command to remove the Functions, Events and Resources that were created.

```
sls remove
```

# About Kumologica

Kumologica is a low code platform to rapidly and safely author lambda functions.

Kumologica is made of two main components:

- **Kumologica Designer**: Flow based tool to create API and integration flows visually. You can download it for free on: [Download](https://kumologica.com/download.html)

- **Kumologica Runtime**: Node library that run your flows in various serverless compute platforms (AWS, Azure, ...)
