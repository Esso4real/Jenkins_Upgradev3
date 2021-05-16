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
        stage('DeployToStaging') {
            when {
                branch 'master'
            }
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'STAGING', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'sudo /opt/apache-tomcat-8.5.66/bin/shutdown.sh  &&  rm -rf /opt/apache-tomcat-8.5.66/webapps/single-module-project.jar && cp /tmp/single-module-project.jar -d /opt/train-schedule /opt/apache-tomcat-8.5.66/webapps/ sudo /opt/apache-tomcat-8.5.66/bin/start.sh', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/tmp', remoteDirectorySDF: false, removePrefix: 'target/', sourceFiles: 'target/single-module-project.jar')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
  
                
                }
            }
        stage('DeployToProduction') {   
             Steps {
        
        sshPublisher(publishers: [sshPublisherDesc(configName: 'PRODUCTION', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'sudo /opt/apache-tomcat-8.5.66/bin/shutdown.sh  &&  rm -rf /opt/apache-tomcat-8.5.66/webapps/single-module-project.jar && cp /tmp/single-module-project.jar -d /opt/train-schedule /opt/apache-tomcat-8.5.66/webapps/ sudo /opt/apache-tomcat-8.5.66/bin/start.sh', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/tmp', remoteDirectorySDF: false, removePrefix: 'target/', sourceFiles: 'target/single-module-project.jar')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
                }
            }
        }
   } 
