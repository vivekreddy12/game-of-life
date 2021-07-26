node('JAVA') {
   stage('SCM') {
        git 'https://github.com/vivekreddy12/game-of-life.git'
   }
   stage('build') {
        sh 'mvn package'
   }
   stage('postbuild') {
        junit '**/TEST-.xml'
        archive '**/*.war'
   }
}
   