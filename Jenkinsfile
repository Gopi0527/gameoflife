pipeline {
    agent { label 'jdk-8'}
    options{
        timeout(time: 30, unit: 'MINUTES')
    }
    triggers{
        pollSCM (* * * * *)
    }
        stages {
            stage('vcs') {
                steps {
                    git url:'https://github.com/Gopi0527/gameoflife.git',
                    branch: 'master'
                }
            }
            stage('build nad package') {
                steps {
                    sh script: 'mvn package'
                }
            }
            stage('reporting') {
                steps {
                    archiveArtifacts artifacts: '**/game0flife.war'
                    junit testResults: '**/target/surefire-reports/TEST-*.xml'
                }
            }
            
        }
    }
