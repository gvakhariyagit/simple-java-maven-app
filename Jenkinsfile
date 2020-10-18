pipeline {
    agent any
    
    environment {
        GIT_VER = getSCMVer()
     //   IMAGE = readMavenPom().getArtifactId()
     //   VERSION = readMavenPom().getVersion()
    }
    stages {
        stage('Github Pull') {
            steps {
                echo 'Pulling from git'
                echo "Git version is $GIT_VER"
                git 'https://github.com/gvakhariyagit/simple-java-maven-app'
            }
        }
        stage('Maven Build') {
            steps {
                echo 'Building Project'
                sh 'mvn clean package'
            }
        }
        stage('Create Docker Image') {
            steps {
                sh 'docker build . -t sampleapp:${VERSION}'
                sh 'docker build . -t sampleapp:1.0.0'
            }
        }
    }
}


def getSCMVer() {
    def gitVer = sh returnStdout: true, script: 'git --version'
    return gitVer 
}
