pipeline{
    agent any
    environment{
        root="/usr/local/go/bin/go"
        branch = "master"
        scmUrl = "https://github.com/iqbalirfanda/sample-go-jenkins.git"
    }

    stages {
        stage("Go Version") {
            steps {
                sh "${root} version"
            }
        }

        stage("Git Clone") {
            steps {
                git branch: "${branch}", url: "${scmUrl}"
            }
        }

        stage("Go Test") {
            steps {
                sh "${root} test ./... -cover"
            }
        }

        stage ( "Go Build") {
            steps {
                sh "${root} build ./... "
            }
        }
    }
}

    // node {
    //     def root = "/usr/local/go/bin/go"

    //         stage 'Checkout'
    //         git url: 'https://github.com/iqbalirfanda/sample-go-jenkins.git'
            
    //         stage 'preTest'
    //         sh "${root} version"
            
    //         stage 'Test'
    //         sh "${root} test ./... -cover"
            
    //         stage 'Build'
    //         sh "${root} build ./..."            
    // }