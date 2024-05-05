pipeline {
    agent any
    tools{
          maven 'maven_3_5_0'
        }

        stages {
            stage('Build') {

                    steps {
                        checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/NormitaRuiz/proyect_java.git']])
						sh 'mvn clean install -DskipTests -P dev'
						archiveArtifacts artifacts: 'target/*.jar'
                    }
            }


            stage('SonarQube') {
                steps {
                     withSonarQubeEnv('sonarqube') { sh "mvn sonar:sonar"}
                     archiveArtifacts artifacts: 'target/*.jar'

                    }
                }

        }
}