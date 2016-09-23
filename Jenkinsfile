#!/usr/bin/groovy

node{

  parallel (
    api: { node {
      
      checkout scm

      stage('build') {
        
        docker.build(
          'api', 
          './api'
        )
      }

      stage('test') {
        
        docker
          .image('api')
          .withRun { c ->
            sh 'ls'
          }
      }

    }},
    services: { node {
      
      checkout scm

      stage('build') {
        
        docker.build(
          'services', 
          './services'
        )
      }

      stage('test') {
        
        docker
          .image('services')
          .withRun { c ->
            sh 'ls'
          }
      }

    }}
  )
}
