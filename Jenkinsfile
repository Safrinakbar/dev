pipeline {
    agent any

    stages {
        stage('scm') {
            steps {
        git branch: 'master', url: 'https://github.com/Safrinakbar/dev.git'
            }
        }
        stage('build') {
            steps {
               shell "mvn clean"
               shell "mvn install"
}
}
stage('build to images') {
            steps {
               script{
                  shell 'docker build -t safrinbaragna/simplewebapp .'
               }
    }
}
stage('push to hub') {
            steps {
               script{
                 withDockerRegistry(credentialsId: 'Docker_cred', url: 'https://index.docker.io/v1/') {
                  shell 'docker push safrinbaragna/simplewebapp'
               }
            }
            }
}
}
}
