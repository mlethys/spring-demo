pipeline {
    agent any
    options {
        ansiColor('xterm')
        timeout(time: 50, unit: 'SECONDS')
        timestamps()
    }
    stages {
        stage('git clone') {
            steps {
                git credentialsId: 'github', url: 'https://github.com/mlethys/spring-demo.git'    
            }
        }
        stage('build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('save tests raports') {
            steps {
                junit '**/target/surefire-reports/TEST-*.xml'
            }
        }
    }
}
