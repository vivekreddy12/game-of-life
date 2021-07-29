pipeline {
    agent { label 'JAVA'}
    triggers {
        cron('H * * * *')
    }
    stages {
        stage('scm') {
            steps {
               git branch: 'master', url: 'https://github.com/vivekreddy12/game-of-life.git'
               mail subject: 'build started'+env.BUILD_ID, to: 'manjula@gmail.com', from: 'vivekreddy@gmail.com' body: 'emledu'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
                stash includes: '**/gameoflife.war', name: 'golwar'
            }
        }
        stage('devserver') {
            agent {label 'REDHAT'}
            steps {
                unstash name: 'golwar'
            }
        }
    }
}