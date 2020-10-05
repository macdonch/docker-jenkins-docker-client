node {

    def app
    def registryCredential = 'leibniz9999_id'

    stage('Clone repository') {
        steps {
            /* repository is defined in the Jenkins pipeline */

            checkout scm
        }
    }

    stage('Build Docker Image') {
        steps {
            app = docker.build("leibniz9999/jenkins-docker-client-lab")
        }  
    }

    stage('Test image') {
        steps {
            app.inside {
                sh 'echo "Tests passed"'
            }
        }
    }

    stage('Push image') {

        steps {

            docker.withRegistry('', registryCredential) {
                app.push("latest")
            }

        }
    }
}