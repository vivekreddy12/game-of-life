
pipeline {
    agent { label 'JAVA'}
    triggers {
         cron ('H * * * *')
    }
    options{
      timeout (time: 10, unit: 'MINUTES')
        retry(2)
    }
    stages {
          stage('scm') { 
            environment {
              DUMMY='FUN'
            }
              steps {
                git branch: 'master', url: 'https://github.com/vivekreddy12/game-of-life.git'
              }
          }
          stage('build') {
               steps {
                 echo env.DUMMY
                 echo env.$GIT_URL
                 timeout (time: 10, unit: 'MINUTES') 
                 retry (3) {
                   sh 'set'
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
             

              