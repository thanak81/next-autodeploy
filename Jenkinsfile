pipeline {
    agent any
    stages {
        stage("Build Docker Container"){
            steps {
                sh "docker build -t thanak81/nextauto ."
            }
        }
        stage("Run Container"){
            steps {
                sh """
                if [ \$(docker ps -q -f name=nextauto) ]; then
                docker stop nextauto
                docker rm nextauto
                fi
                """
                sh "docker run -d -p 3003:3000 --name nextauto thanak81/nextauto"
            }
        }
    }

}