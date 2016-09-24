#!/usr/bin/groovy

def imageTag = "${env.BRANCH_NAME}.${env.BUILD_NUMBER}"

stage "Build" {
  
    parallel {
      api: {
        node {
          
          checkout scm
  
          docker
            .build(
              "massiveco/api:${imageTag}", 
              "./api"
            )
            .push()
        }
      }
    }
}

stage "Test" {
  
  parallel {
      api: {
        node {
          
          docker
            .image("massiveco/api:${imageTag}")
            .withRun { c ->
              sh 'ls'
            }
        }
      }
    }
}
