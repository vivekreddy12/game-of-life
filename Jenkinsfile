pipeline {
    agent { label 'JAVA'}
    triggers {
        cron('H * * * *')
    }
    stages {
        stage('scm') {
            steps {
               git branch: 'master', url: 'https://github.com/vivekreddy12/game-of-life.git'
               mail subject: 'build started' +env.BUILD_ID, to: 'manju.poreddymail.com', from: 'vivekreddysandhi@gmail.com', body: 'emledu'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
        
    }
}