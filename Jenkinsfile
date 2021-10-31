ipeline{
    
    tools{
        dockerTool 'mydocker'
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
                    echo "BUILDING THE DOCKER IMAGE"
                    echo "Deploying version ${params.VERSION}"
                    withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                        sh 'sudo docker build -t 23gardasvinay116/java-mvn-hanuman:$BUILD_NUMBER .'
                        sh 'sudo sudo docker login -u $USER -p $PASS'
                        sh 'sudo docker push 23gardasvinay116/java-mvn-hanuman:$BUILD_NUMBER'
                }
            }
        }
         }
        stage("DEPLOY"){
            
            
            steps{
                script{
                    echo "Deploying the app"
                    echo "Deploying version ${params.VERSION}"
                }
            }
    }
}
    }
	
