
pipeline {
    agent { label 'JAVA'}
    triggers {
         cron ('H * * * *')
         pollSCM ('* * * * *')
    }
    stages {
          stage('scm') { 
            environment {
              DUMMY='FUN'
            }
            options{
              timeout (time:1,unit:'HOURS')
              entry(2)
            }
            steps {

                git branch: 'master', url: 'https://github.com/vivekreddy12/game-of-life.git'
               }
          }
          stage('build') {
               steps {
                 echo env.DUMMY
                 echo env.$GIT_URL
                 timeout(time:10, unit: 'MINUTES') {
                 retry (3) {
                   sh 'mvn package'

                 } 
               }
          }
     }
          post {
            success{
              archive '**/gameoflife.war'
              junit '**/TEST-*.xml'
            }
          }
}
        

     
    
