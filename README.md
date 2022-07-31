# Hosting a Full-Stack Application
This is a deployment project as part of the Udacity nanodegree program; advanced full-stack web development. The full-stack application was afforded by the program, and I was given the opportunity to work on it. More details are displayed in the following sections, and also, you can **visit the following link to preview the application:**
> - http://udegram.s3-website-us-east-1.amazonaws.com

---

## **Infrastructure**

![The infrastructure of the application](/docs/Deployment_Architecture.png "The infrastructure of the application")

We can look at the application from both ends: developer and user. **For the developer:**

- The developer commits his code to github so that CircleCI following the repository can build the application. After validating IAM permissions, the application is ready to be deployed: the server to elastic beanstalk, and the static website to AWS S3. The server is sending and receiving data from the AWS RDS, and as well, transfer requests back and forth from the AWS S3.

**Meanwhile for the user:**

- The user can visit the website, and the application will be served from the AWS S3. And the same connections apply in the background to serve the user with the data and pages required.

## **Dependencies**

```
- Node v14.15.1 (LTS) or more recent. While older versions can work it is advisable to keep node to latest LTS version

- npm 6.14.8 (LTS) or more recent, Yarn can work but was not tested for this project

- AWS CLI v2, v1 can work but was not tested for this project

- A RDS database running Postgres.

- A S3 bucket for hosting uploaded pictures.

```

## **Pipeline**

`CircleCI` is following the repository on the master branch for any changes so once the developer commits the changes, the pipeline will start ahead with the workflow:

- Build the application:
  1. Install NodeJS and NPM.
  1. Install the Front-End dependencies.
  1. Install the API dependencies.
  1. Lint the Front-End code.
  1. Build the Front-End application.
  1. Build the API application.
- Hold and wait for approval before deployment.
- Deploy the application:
  1. Install NodeJS and NPM.
  1. Setting up Elastic Beanstalk.
  1. Setting up AWS cli.
  1. Setting elastic beanstalk environment variables.
  1. Deploy the API to Elastic Beanstalk.
  1. Deploy the Front-End to AWS S3.

### Installation

Provision the necessary AWS services needed for running the application:

1. In AWS, provision a publicly available RDS database running Postgres. <Place holder for link to classroom article>
1. In AWS, provision a s3 bucket for hosting the uploaded files. <Place holder for tlink to classroom article>
1. Export the ENV variables needed or use a package like [dotnev](https://www.npmjs.com/package/dotenv)/.
1. From the root of the repo, navigate udagram-api folder `cd starter/udagram-api` to install the node_modules `npm install`. After installation is done start the api in dev mode with `npm run dev`.
1. Without closing the terminal in step 1, navigate to the udagram-frontend `cd starter/udagram-frontend` to intall the node_modules `npm install`. After installation is done start the api in dev mode with `npm run start`.

## Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd starter/udagram-frontend`
1. `npm run test`
1. `npm run e2e`

There are no Unit test on the back-end

### Unit Tests:

Unit tests are using the Jasmine Framework.

### End to End Tests:

The e2e tests are using Protractor and Jasmine.

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework
