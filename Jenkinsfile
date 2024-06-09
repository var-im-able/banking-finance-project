pipeline {
    agent any
    stages{
        stage('Cloning the Finance project from my GitHub'){
            steps{
                git url:'https://github.com/var-im-able/banking-finance-project.git'
            }
        }

        stage('Clean Packaging the code to create .jar file'){
            steps{
                sh 'mvn clean package'
            }
        }
        
        stage('Creating application image (from Dockerfile)'){
            steps{
                script{
                    sh 'docker build -t bankingapplication .'
                    sh 'docker images'
                }
            }
        }

        stage('Containerizing the application image to run on binded port 8082 '){
            steps{
                sh 'docker run -itd --name DIP -p 8082:8081 bankingapplication'
            }
        }

        stage('Renaming the image and pushing to DockerHub'){
            steps{
                script{
                        sh 'docker tag bankingapplication varsanandocks/financeproject:new'
                        sh 'sudo docker push  varsanandocks/financeproject:new'
                }

            }
        }


   }
}