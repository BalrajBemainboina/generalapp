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
                    rtUpload (
                        serverId: 'balrajnikhildevops',
                        spec: '''{
                                "files": [
                                    {
                                        "pattern": "generalartifactapp*.zip",
                                        "target": "example-repo-local/"
                                    }
                                ]
                            }'''
                    )                   
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                sh 'ansible-playbook ${playbook_name} -i inventories.yml'
            }
        }
    }
}
