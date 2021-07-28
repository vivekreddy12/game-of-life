
pipeline {
    agent { label 'JAVA'}
    triggers {
         cron ('H * * * *')
         pollSCM ('* * * * *')
    }
    parameters { choice(name: 'MAVEN', choices: ['package', 'compile', 'clean package'], description: 'to build perameter') }
    stages {
          stage('scm') {
            steps {

                git branch: 'master', url: 'https://github.com/vivekreddy12/game-of-life.git'
               }
          }
          stage('build') {
               steps {
                 echo env.$GIT_URL
                 sh 'mvn package' 
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
        

     
    
