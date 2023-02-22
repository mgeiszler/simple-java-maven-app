pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '. /etc/profile.d/maven.sh; pwd; ls -l; mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh '. /etc/profile.d/maven.sh; pwd; ls -l; mvn test'
            }
            //post {
            //    always {
            //        sh '. /etc/profile.d/maven.sh; pwd; ls -al; junit target/surefire-reports/*.xml'
            //    }
            //}
        }
        stage('Deliver') {
            steps {
                sh '. /etc/profile.d/maven.sh; pwd; ls -al; ./jenkins/scripts/deliver.sh'
            }
        }
    }
}
