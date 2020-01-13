#!/bin/env groovy

node {
    deleteDir()

    checkout scm

    files = sh(returnStdout: true, script: 'ls')
    println "list of property files"
    p_files = files.split("\n").collect()[1,2]

    
    properties([buildDiscarder(logRotator(numToKeepStr: '100')),
    	parameters([
		choice(choices: p_files, description: 'test test', name: 'param_files'),
		[$class: 'CascadeChoiceParameter', choiceType: 'PT_SINGLE_SELECT', name: 'main_param', referencedParameters: 'param_files',
			script: [$class: 'GroovyScript', script: [classpath: [], sandbox: false, script: '''file = ${param_files}
				content = sh(returnStdout:true, script: \'cat ${file}\')
				return content''']]]
    	])])
    
    sh 'echo Hello World!'
}