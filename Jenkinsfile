#!/bin/env groovy

node {
    deleteDir()
    
    checkout scm

    files = sh(returnStdout: true, script: 'ls')
    println "list of property files"
    println files.split()


    properties([buildDiscarder(logRotator(numToKeepStr: '100'))])
    
    sh 'echo Hello World!'
}
