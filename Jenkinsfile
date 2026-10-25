
pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {
        stage('Build') {
            steps {
                echo '----------- build started ----------'
                sh 'mvn clean package -Dmaven.test.skip=true'
                echo '----------- build completed ----------'
            }
        }

        stage('Test') {
            steps {
                echo '----------- unit test started ----------'
                sh 'mvn test'
                echo '----------- unit test completed ----------'
            }
        }

        stage('SonarCloud Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        /opt/maven/bin/mvn \
                          org.sonarsource.scanner.maven:sonar-maven-plugin:5.8.0.7211:sonar \
                          -Dsonar.organization=sonarqubepractice-c07 \
                          -Dsonar.projectKey=saidemy01-keyy_TestProject \
                          -Dsonar.host.url=https://sonarcloud.io
                    '''
                }
            }
        }
    }
}

