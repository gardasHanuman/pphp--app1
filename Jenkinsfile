pipeline{
    
    tools{
        dockertool 'mydocker'
    }
    agent none
    environment{
        IMAGE_NAME='23gardasvinay116/java-mvn-hanuman:php$BUILD_NUMBER'
    }
    stages{
        stage("Build the docker image for php"){
            agent any
            steps{
                script{
                    echo "Building the docker image"
                    sh 'sudo systemctl start docker'
                    withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                        sh "sudo docker build -t ${IMAGE_NAME} ."
                        sh 'sudo sudo docker login -u $USER -p $PASS'
                        sh "sudo docker push ${IMAGE_NAME}"
                }
                }
            }
        }
        stage("Deploy app via dockercompose file"){
            agent {label 'linux_slave'}
            steps{
                script{
                    echo "deploy with dockercompose"
                     sh 'sudo systemctl start docker'
                    sh "bash ./remote-server.sh ${IMAGE_NAME}"
                }
            }
        }
    }
}
© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
