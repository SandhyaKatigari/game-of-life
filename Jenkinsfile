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
