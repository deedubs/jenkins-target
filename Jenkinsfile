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
          .inside {
            sh 'ls'
          }
      }

    }}
  )
}
