pipeline {
    agent any
        //docker {
        //    image 'maven:3-alpine' 
        //    args '-v /root/.m2:/root/.m2' 
        //}
    stages {
        stage('Build') {
            steps {
                bat("mvn -B -DskipTests clean package")
            }
        }
        stage('Test') {
            steps {
			// sh 'mvn test'
                bat("mvn test")
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
			// sh './jenkins/scripts/deliver.sh'
                bat(".\\jenkins\\scripts\\deliver.sh")
            }
        }
    }
}