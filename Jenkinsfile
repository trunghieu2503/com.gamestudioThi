pipeline {
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout scm
                sh 'chmod +x ./gradlew' // Đặt quyền thực thi ngay sau khi checkout
            }
        }
        stage('Build') {
            steps {
                sh './gradlew clean build' // Biên dịch dự án trước
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarSever') {
                    sh './gradlew sonar' // Gọi phân tích SonarQube sau khi đã biên dịch  ok
                }
            }
        }
    }
}
