#!/usr/bin/groovy

node{
  stage 'Build'

  parallel (
    api: { node {
      checkout scm

      docker.build "api:snapshot"
    }},
    services: { node {
      checkout scm
      sh """
        cd services
        docker build -t services .
      """
    }}
  )
}