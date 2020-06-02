node('Build'){
    stage('scm'){
        git 'https://github.com/SandhyaKatigari/game-of-life.git'

    }

    stage('build'){
        sh label: '', script: 'mvn package'
        stash name: 'gol-war', includes: 'gameoflife-web/target/gameoflife.war'

    }

    stage('postbuild'){
        archiveArtifacts 'gameoflife-web/target/*.war'
        
    }

}
node('Dev'){
   stage('scm'){
      unstash 'gol-war'
      sh label: '', script: 'ansible-playbook -i /home/sandhya/testing/hosts /home/sandhya/testing/test.yml'
      stash name: 'ansible-file', includes: '/home/sandhya/testing/test.yml'
      
   }
}

