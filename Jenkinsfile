pipeline {
    agent any

    stages {
        stage('Maven WAR Build') {
            steps {
                sh '/opt/maven/bin/mvn package'
            }
        }
    }
}
