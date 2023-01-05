pipeline {
    agent any

    stages {
        
        stage('Update Version & Build') {
            steps {
                echo 'Trigerring POM Version update to next version'
                sh './bump_pom_version.sh'
            }
        }
        stage('Push to Jfrog Artifactory') {
            steps {
                    echo 'pushed to artifactory'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'DEPloyment to be triggered here.'
            }
        }
    }
}
