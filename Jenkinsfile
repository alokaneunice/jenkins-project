pipeline{
    agent any
stages{
    stage("GitHub checkout....") {
        steps {
            script {
                git branch: 'main', url: 'https://github.com/alokaneunice/jenkins-project.git'
            }
        }
    }
    stage("Build docker connecting....."){
        steps{
            sh 'printenv'
            sh 'git version'
            sh 'docker build . -t engrvic/image-app1.1'
        }
    }
    stage("push image to DockerHub"){
        steps{
            script {
                withCredentials([string(credentialsId: 'DOCKERID', variable: 'DOCKERID')]) {
                    sh 'docker login -u engrvic -p ${DOCKERID}'
                }
                sh 'docker push engrvic/image-app1.1:latest'
            }
        }
    }
}
}