# Objectives of the workshop

The objectives of this workshop is to manipulate Jenkins to have a better understanding of it.

Once installed, we will create some pipelines (and install some plugins) to validate various aspects of Jenkins.

# Steps

## Step 1

Download and install Jenkins [Product page](https://www.jenkins.io/doc/book/installing/).

Be careful to unlock Jenkins and customize it with recommanded plugins (Pipeline plugin).

## Step 2

Just to be sure that the Pipeline plugin is correctly set, and to discover the syntax of Pipeline, create an Hello World Pipeline.

The main concepts of Jenkins Pipelines are described [here](https://www.jenkins.io/doc/book/pipeline/).

To create your first Hello World Pipeline, the process is described [here](https://www.jenkins.io/doc/book/pipeline/getting-started/).

Launch the pipeline and check it is working as expected.

Now create the same Pipeline in the Jenkinsfile of a Github repository.

Push a change on this repository and check that the Pipeline is launched.

## Step 3

Now we will improve the last Pipeline we created.

Actually we will make the repository a real Java Maven project.

We will add some unit tests in this project.

Then we define new stages in the Pipeline, with a package step, and a test step.

You will have to configure environment variables and settings so that Jenkins use appropriate Java and Maven installations.

You can find a guided tour of Jenkins Pipeline [here](https://www.jenkins.io/doc/pipeline/tour/getting-started/) that can help you.

Take car, in the guided tour, they suppose you can define Docker-based agents for your pipeline.

It is simpler at the beginning to use local Java and Maven installations for your agents.

## Step 4 (optional)

Connect to [SonarCloud](https://sonarcloud.io/) with your Github account (or create a dedicated account).

Create a token for your account following this [procedure](https://docs.sonarqube.org/latest/user-guide/user-token/).

Install SonarScanner plugin on your Jenkins.

Configure it following this [guide](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-jenkins/) by storing your token in Jenkins.

Set appropriate sonar properties in your pom.xml.

Add a dedicated step in your Jenkinsfile to launch SonarQube analysis (Find help in this [guide](https://www.jenkins.io/doc/pipeline/steps/sonar/)).

See that results are build on SonarCloud after launching the pipeline.

## Step 5 (optional)

If you have Docker installed on your environment, you can install Jenkins docker plugins.

This will allow you to set a specific agent that will run your pipeline in a given docker image.

Then define and launch manually a pipeline running in a docker container.

You can find help [here](https://www.jenkins.io/doc/book/pipeline/docker/).

## Step 6

The purpose is to create a realistic CD (Continuous Delivery) Pipeline.

This pipeline will define various step :
- build the project
- test the project
- release the project (thanks to the maven release plugin)

The maven release plugin does the following job :
- sets a non snapshot version in the pom
- tags and pushes this tag in github
- deploys the built artifact in nexus
- sets a new snapshot version in the pom
- pushes this version in github

You can find documentation on the release plugin [here](https://maven.apache.org/maven-release/maven-release-plugin/).

Study this [repo](https://github.com/rgirodon/tse_mvn_nexus) that does this, and try to reproduce it on your local Jenkins / Nexus platform.

Take note of the usage of params for the build, asked to the user before a launch.

See a doc [here](https://www.jenkins.io/doc/book/pipeline/syntax/) for a reference documentation on pipeline syntax.
