# Tested Piplelines
##
- Simple pipeline - https://github.com/brainupgrade-in/devops-azure/blob/main/pipelines/simple.yml
##
- Multi OS - https://github.com/brainupgrade-in/devops-azure/blob/main/pipelines/multi-os.yml
- Multi stages jobs - https://github.com/brainupgrade-in/devops-azure/blob/main/pipelines/multi-stages-jobs.yml
- Multi container - https://github.com/brainupgrade-in/devops-azure/blob/main/pipelines/multi-targets-containers.yml
##
- Matrix Strategy OS - https://github.com/brainupgrade-in/devops-azure/blob/main/pipelines/matrix-strategy-multi-os.yml
- Matrix Strategy Containers - https://github.com/brainupgrade-in/devops-azure/blob/main/pipelines/matrix-strategy-containers.yml
##
- Java 11 Maven Package - https://github.com/brainupgrade-in/request-logger/blob/main/.ado/maven-package.yml
- Java 11 Maven Package Test - https://github.com/brainupgrade-in/request-logger/blob/main/.ado/maven-package-junit.yml
- Docker build - https://github.com/brainupgrade-in/weather-py/blob/main/.ado/docker-build.yml

## 
- CodeQL (codespace agent) - https://dev.azure.com/brainupgradein/_git/request-logger?path=/azure-pipelines-codeql.yml&version=GBmain  (Results - Azure Repos -Adv Security)

##
- Templatized jobs - https://github.com/brainupgrade-in/devops-azure/blob/main/pipelines/templates/job-template-step-conditional/main.yml
##
- Java Test Code Coverage - https://github.com/brainupgrade-in/spring-petclinic/blob/main/.ado/build-test.yml
##
- Sonar Scan - https://github.com/brainupgrade-in/spring-petclinic/blob/main/.ado/sonar.yml
## 
- Image Scanning - https://github.com/brainupgrade-in/gitops-apps-hello/blob/main/.ado/image-scan.yml

# 
- PR - Docker build scan push - https://github.com/brainupgrade-in/gitops-apps-hello/blob/main/.ado/trigger-pr.yml

# 
- k8s deploy e2e - https://github.com/brainupgrade-in/gitops-apps-hello/blob/main/.ado/k8s-deploy-e2e-environment.yml