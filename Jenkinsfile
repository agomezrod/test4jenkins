pipeline {
    agent { label 'jenkinslave' }
    stages {
        stage ('Fetch dependencies') {
            steps {
                sh "sudo docker pull nginx:latest"
            }
        }
        stage ('Build docker image') {
            steps {
                sh "sudo docker build . -t customnginx:1"
            }
        }
        stage ('Test image') {
            steps {
                sh 'echo "test successful"'
            }
        }
        stage ('Push image to OCIR') {
            steps {
                sh "sudo docker login -u 'REGISTRY USERNAME' -p 'REGISTRY TOKEN' fra.ocir.io"
                sh "sudo docker tag customnginx:1 fra.ocir.io/odemeasouth/nginx:custom"
                sh "sudo docker push fra.ocir.io/odemeasouth/nginx:custom"
            }
        }
        
    }
}
