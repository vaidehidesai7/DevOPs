pipeline {
    agent any

    stages {
        stage('Code Pull') {
            steps {
                //pulling code from git repository
                git branch: 'main', url: 'https://github.com/vaidehidesai7/DevOPs.git'
            }
        }
        stage('Image Build') {
            steps {
                //building image
                sh 'docker build -t my_image:latest .'
            }
        }
        stage('Push Image') {
            steps {
                //pushing image to container repository (Dockerhub)
                withCredentials([usernamePassword(credentialsId: 'dockerhub_pass', 
                                    passwordVariable: 'PASS', 
                                    usernameVariable: 'USER')]) {
                sh "docker login -u ${USER} -p ${PASS}"
                sh 'docker tag my_image:latest s4432496/my_image1:latest'
                sh 'docker push s4432496/my_image1:latest'
                }
            }
        }
        stage('Deploy') {
          steps {
                //deploying using kubectl
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
                sh 'kubectl rollout restart deployment my-app-deployment'
                sh 'nohup kubectl port-forward --address 0.0.0.0 service/my-app-service 30007:80 > pf.log 2>&1 &'
            }
        }
    }
}

