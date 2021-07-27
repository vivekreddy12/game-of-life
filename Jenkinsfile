pipeline {
    agent { label 'JAVA'}
    stages {
          stage('scm') {
            steps {

                git branch: 'master', url: 'https://github.com/vivekreddy12/game-of-life.git'
               }
          }
        stage('build') {
               steps {
                 sh 'mvn package'
               }
          }
     }
     post {
        sucess{
             archive '**/gameoflife.war'
             junit '**/TEST-*.xml'
        }
    }
}
        

     
    
