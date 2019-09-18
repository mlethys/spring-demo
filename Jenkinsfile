node {
     timestamps {
      stage('Git clone') {
         deleteDir()
         checkout scm
     }
    stage('build') {
        sh 'mvn clean package'
    }
     stage('save tests raports') {
       junit '**/target/surefire-reports/TEST-*.xml'
    }
     }  
}
