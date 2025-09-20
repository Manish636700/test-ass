pipeline {
    agent any

    tools {
        // Make sure these names exist in Jenkins -> Manage Jenkins -> Tools
        maven "Maven-3.8.6"
        jdk "JDK21"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/adarsh19961105/porbis-assessment.git', credentialsId: 'github'
            }
        }

        stage('Build with Nexus') {
            steps {
                configFileProvider([configFile(fileId: 'maven-settings-nexus',variable: 'MAVEN_SETTINGS' )]){
                    sh """
                    mvn clean install --settings "$MAVEN_SETTINGS" 
                    """
                }
            }
        }

        stage('Test') {
            steps {
                sh 'mvn -B test'
            }
            post {
                always {
                    junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {
            steps {
                sh 'mvn -B package -DskipTests'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'target/*.war', fingerprint: true
                }
            }
        }
    }
    post {
        success {
            echo 'Build and Test Successful. Artifact Archived.'
        }
    }
}
