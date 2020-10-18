pipeline {
    agent any
    
    environment {
        GIT_VER = getSCMVer()
 //       IMAGE = readMavenPom().getArtifactId()
 //////       VERSION = readMavenPom().getVersion()
    }
    stages {
        stage('Github Pull') {
            steps {
                echo 'Pulling from git'
                echo "Git version is $GIT_VER"
                git 'https://github.com/devops-max/simple-java-maven-app'
            }
        }
        stage('Maven Build') {
            steps {
                echo 'Building Project'
                sh 'mvn clean package'
            }
        }
    }
}


def getSCMVer() {
    def gitVer = sh returnStdout: true, script: 'git --version'
    return gitVer 
}
