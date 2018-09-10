#!/usr/bin/env groovy

stage('build') {
    node('node && ios && android') {
        deleteDir()
        checkout scm
        sh "npm ci"

        def seyConfig = []
        seyConfig << "SEY_VERBOSE=1"
        seyConfig << "SEY_NOBROWSERIFY=1"

        withEnv(seyConfig) {
            sh "npx seymour"
        }
    }
}
