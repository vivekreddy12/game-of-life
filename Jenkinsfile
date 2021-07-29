pipeline {
    agent { label 'JAVA'}
    triggers {
        cron('H * * * *')
    }
    environment {
        CI_ENV = 'DEV'
    }
    stages {
        stage('scm') {
            environment {
                DUMMY = 'FUN'
            }

            steps {
               git branch: "${params.BRANCH}", url: 'https://github.com/vivekreddy12/game-of-life.git'
                echo env.CI_ENV
                echo env.DUMMY
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
                stash includes: '**/gameoflife.war', name: 'golwar'
            }
        }
        stage('devserver'){
            agent {label 'REDHAT'}
            steps {
                unstash name: 'golwar'
            }
        }
    }
}