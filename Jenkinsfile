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
                
                sshPublisher(publishers: [sshPublisherDesc(configName: 'STAGING', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'sudo /opt/apache-tomcat-8.5.66/bin/shutdown.sh  &&  rm -rf /opt/apache-tomcat-8.5.66/webapps/single-module-project.jar && cp /tmp/single-module-project.jar /opt/apache-tomcat-8.5.66/webapps/ sudo /opt/apache-tomcat-8.5.66/bin/start.sh', remoteDirectory: '/tmp', removePrefix: 'target/', sourceFiles: 'target/single-module-project.jar')])])
            }
        }
      

        stage('DeployToProduction') {   
             steps {
        
        sshPublisher(publishers: [sshPublisherDesc(configName: 'PRODUCTION', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'sudo /opt/apache-tomcat-8.5.66/bin/shutdown.sh  &&  rm -rf /opt/apache-tomcat-8.5.66/webapps/single-module-project.jar && cp /tmp/single-module-project.jar /opt/apache-tomcat-8.5.66/webapps/ sudo /opt/apache-tomcat-8.5.66/bin/start.sh', remoteDirectory: '/tmp', removePrefix: 'target/', sourceFiles: 'target/single-module-project.jar')])])
                }
            }
        }
   } 
  
