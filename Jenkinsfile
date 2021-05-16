pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh 'mvn -f maven-samples/single-module/pom.xml clean package'
                archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
            }
        }
    }
}
