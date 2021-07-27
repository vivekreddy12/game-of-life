pipeline {
     agent { label 'GOM'}
     stages {
          stage ('SCM'){
             steps {
                
               git branch: 'master','https://github.com/vivekreddy12/game-of-life.git'
             } 
          stage ('build'){
             steps {
                    sh 'mvn package'
             }
          
          
          }
     }
}     

     
             