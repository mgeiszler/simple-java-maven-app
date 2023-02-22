pipeline {
    agent any
    stages {
        stage("Clean up from previous build") {
            steps {
                deleteDir()
            }
        }
        stage('Build') {
            steps {
                sh '. /etc/profile.d/maven.sh; mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh '. /etc/profile.d/maven.sh; mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
