#!/usr/bin/groovy

node{
  stage 'Build'

  parallel (
    api: { node {
      checkout scm
      sh """
        cd api
        docker build -t api .
      """

    }},
    services: { node {
      checkout scm
      sh """
        cd services
        docker build -t services.
      """
    }}
  )
}