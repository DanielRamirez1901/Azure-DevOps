Devops Project


- 1. Command 
    mvn clean install
in webapp/target/ u find the webapp.war

![Image1](images/image1.png)

- 2. Create a build pipeline

In azure devops portal, go to pipelines and then, create one

![Image2](images/image2.png)

In connect, we select github

![Image3](images/image3.png)

In select u select the repo that u need o want to have connected with this pipeline

In this example, this repo is a java based project so we are going to select in configurations a maven pipeline

![Image4](images/image4.png)

we can run the maven pipeline example given by azure for the moment

azure-pipelines.yml```

    # Maven
    # Build your Java project and run tests with Apache Maven.
    # Add steps that analyze code, save build artifacts, deploy, and more:
    # https://docs.microsoft.com/azure/devops/pipelines/languages/java

    trigger:
    - master

    pool:
    vmImage: ubuntu-latest

    steps:
    - task: Maven@3
    inputs:
        mavenPomFile: 'pom.xml'
        mavenOptions: '-Xmx3072m'
        javaHomeOption: 'JDKVersion'
        jdkVersionOption: '1.8'
        jdkArchitectureOption: 'x64'
        publishJUnitResults: true
        testResultsFiles: '**/surefire-reports/TEST-*.xml'
        goals: 'package'

```

and then, we can press save and run
