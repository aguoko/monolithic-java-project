pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'muna', path: '', url: 'http://18.130.124.210:8080')], contextPath: 'okougwu', onFailure: false, war: '**/*.war'
            }
        }
    }
}
