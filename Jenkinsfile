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
                
sshPublisher(publishers: [sshPublisherDesc(configName: 'STAGING', sshCredentials: [encryptedPassphrase: '{AQAAABAAAAAQTR/4YzfOrkd0Fmk03v9EOh9Vm1RdFOXaK23lyPiPA28=}', key: '''-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAmsol04YADr2Ps4x3HQcD/wRUOaZ4+LtAsLBdKllZ80a1C9kR
oEtFN7ezn4+YVQ55QpefaZ37jQdj+aDny9s2+KIjaqGZ2BmLm43GXxT8Ccsk+ncT
jhlC/J+ie8qq8UwIXllQgIrc0G5uhuaQzOgqZUSZjV0vXHmwooVQDebtB+QQXK7v
Xm8Pap73HA1uy76axlMfD/N88xjQXa6vHwVg7rvScaS3GKv3kGz0GRo54I+C1Zhz
V0H968svA4vfYtIUDElLgfmxTpl09bWZz8Xu4b2+C6A3bso7G3Z2+GWZ3MTVOTEK
4oBzf/7v8EZA+Pakbew65g7q/xKV1woICaIhUwIDAQABAoIBAFmQeFyxX50n4Fty
/oUkRxKrTZTiF4NMzjyuf+n+M4cJtb56RrGqfA2mVOARtYIZ0t5OX2Y8jI5o5VdO
3HDfkipBnx6XDS62cUp7uXnQ6Zk9G1N1zTHeuhz0vY7FkS334au+IE+Qif5st7WE
+eomuElKbVMXxUzL+QHBA7ZXlXWHgfEECu11VDjY0nvJmGqBDwXvBuh/qLSNnfCd
ecGlTEy2gsB6uNlohS4yIWT1SFlkMwFPuL1jfDiq5WIiYrnyihRpdQTST5UKIwon
DD+qonkTSKjcny2vymOymXcGURJDTvF59GOL2CYeyJskMsjSgX/JJnKYrE1M/8IE
qSQVLVECgYEAybXxUYP0ULwbxmlXultOaSLC+zGvq+KR/DVJv+iKJMp2qVMNXw4d
Jhme0OI58IXqNl602kl2ZmkYW9JEwoHJISCnTr5kbsxJdRwzydU1lJMBbmKV3/J2
WkfES0T+P4q8Pa2NOGvn3pNk5/2iIbGx3+zFgk1T00zgDQwTqcDnj8kCgYEAxHNM
ktUmu3sHrIg0qs4XCBErgX/UbrySEocPG6csZE11YsB15B79g98Ve8x8BvYfFq0+
AVjxzDT0Y57cDTVAFwLODd5sHEh/+HnJKp4y/Ljca43P7Rb6GQnG/v4Fy5UulaLs
pQ2xTHsWDaHviWbr6Q77mEudYDpJSok/G6CvDjsCgYEAq34jwGFGy4lSt/sCGi/c
12g1i+lvaNzFrz8DB8VGBgeYoVc6LBHM2IK50vAzwHmqajVU363Lm0BI9HAuA4zi
mmavuDQJIWZQIeAra7L4zeu6MMZilDcJRrJzgmcTHqTubCXsxgZ/6W05QkASo0D3
cOFV/vWNij1208Drysx2U3kCgYAhNPQupcUkT8meSm/Mp4WRIYXfIAKCrXFrnFTb
cci5M7ax+KJ06yAjWGRDRu94JcZfiO1AQQ6uXA0rgcDkoqmwuhKmmYBgz4iCMePl
RlSMD5uCurf49bdU4Cg5FitYnGEBfkbOJ6BeszepGkRpT3J1NMkmlzGFAJU++jAm
tWSh3QKBgQCsArmnJ3mTxFDnpWcTgBDo08hIrVvUvJ1HnyVUWm9W1RWtZA0MF1eU
7brYLQ/yKRJqi8EupuvdWGmVQ3lEC7ymxfJFtt4xg5G+rPw+VkgMekcJs1r2gUxp
+4+S1u7BgrZRIgCrte8R8z/J2SfmDOfraOL1yvG0pEF3u4sQXQRmlw==
-----END RSA PRIVATE KEY-----
''', keyPath: '', username: 'root'], sshRetry: [retries: 2, retryDelay: 10000], transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'sudo cd /opt/apache-tomcat-8.5.66/bin/ && ./shutdown.sh  &&  rm -rf /opt/apache-tomcat-8.5.66/webapps/single-module-project.jar && cp /tmp/single-module-project.jar /opt/apache-tomcat-8.5.66/webapps/ && sudo cd /opt/apache-tomcat-8.5.66/bin/ && ./start.sh', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/tmp', remoteDirectorySDF: false, removePrefix: 'target/', sourceFiles: 'target/single-module-project.jar')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])


                }
            }
        }
    }
