#!/usr/bin/env groovy

stage('build') {
    node('node && ios && android') {
        deleteDir()
        checkout scm
        sh "npm ci"

        sh "pushd ./node_modules/cordova-fetch; patch -p0 < ../../fetch.patch; popd"

        def seyConfig = []
        seyConfig << "SEY_VERBOSE=1"
        seyConfig << "SEY_NOBROWSERIFY=1"

        withEnv(seyConfig) {
            sh "npx seymour"
        }
    }
}
