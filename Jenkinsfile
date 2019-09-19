node {
     timestamps {
      stage('Git clone') {
         checkout scm
     }
    stage('build') {
        sh 'mvn clean package'
    }
     stage('save tests raports') {
       junit '**/target/surefire-reports/TEST-*.xml'
    }
    stage('build docker') {
        sh '''eval $(minikube docker-env)
        mvn compile jib:dockerBuild'''
    }
    stage('Deploy to test') {
        sh 'kubectl create deployment spring-demo --image=spring-demo:0.0.1-SNAPSHOT'
        sh 'kubectl expose deployment spring-demo --type=NodePort --port=8090'
    }
     }  
}
