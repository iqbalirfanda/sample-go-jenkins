// pipeline{
//     agent any
//     environment{
//         root="/usr/local/go/bin/go"
//         branch = "master"
//         scmUrl = "https://github.com/iqbalirfanda/sample-go-jenkins.git"
//     }

//     stages {
//         stage("Go Version") {
//             steps {
//                 sh "${root} version"
//             }
//         }

//         stage("Git Clone") {
//             steps {
//                 git branch: "${branch}", url: "${scmUrl}"
//             }
//         }

//         stage("Go Test") {
//             steps {
//                 sh "${root} test ./... -cover"
//             }
//         }

//         stage ( "Go Build") {
//             steps {
//                 sh "${root} build ./... "
//             }
//         }
//     }
// }

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



    // challenges
pipeline{
    agent any
    environment {
        imageName = "my-sample-go-jenkins"
        containerName = "sample-go-jenkins"
        branch = "master"
        scmUrl =  "https://github.com/iqbalirfanda/sample-go-jenkins.git"
    }
    stages {
        stage("Cleaning up") {
            steps {
                echo 'Cleaning up'
                sh 'docker rm -f "${containerName}" || true'
            }
        }

        stage("Clone Source") {
            steps {
                echo 'Clone Source'
                git branch: "${branch}", url: "${scmUrl}"
            }
        }

        stage("Docker build") {
            steps {
                echo 'Compiling and building'
                sh 'docker build -t "${imageName}" .'
            }
        }

        stage("Docker run") {
            steps {
                echo 'Go run'
                sh 'docker run --name "${containerName}" ${imageName}'
            }
        }

        stage("Docker run test") {
            steps {
                echo 'Go test'
                sh 'docker run ${imageName} sh -c "go test"'
            }
        }
    }
}