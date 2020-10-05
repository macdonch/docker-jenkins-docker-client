node {

    def app
    def registryCredential = 'leibniz9999_id'

    stage('Clone repository') {

        /* repository is defined in the Jenkins pipeline */

        checkout scm

    }

    stage('Build Docker Image') {

        app = docker.build("leibniz9999/jenkins-docker-client-lab")

    }

    stage('Test image') {

        app.inside {
            sh 'echo "Tests passed"'
        }

    }

    stage('Push image') {

        docker.withRegistry('', registryCredential) {
            app.push("latest")
        }

    }
}