#!/usr/bin/env groovy

node{
    stage('Git Checkout'){
        git 'https://github.com/skani-git/DevOpsClassCodes.git'
    }
    stage('Compile'){
        withMaven(maven:'Maven'){
            sh 'mvn compile'
        }
    }
    stage('Test'){
        try{
            withMaven(maven:'Maven'){
                sh 'mvn test'
            }
        } finally{
            junit 'target/surefire-reports/*.xml'
        }
    }
    stage('Package'){
        withMaven(maven:'Maven'){
            sh 'mvn package'
        }
    }
}
