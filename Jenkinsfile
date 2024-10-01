pipeline {
    agent any
    
    tools {
        flutter 'flutter-sdk' // Assuming 'flutter-sdk' matches your configured Flutter SDK tool in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ahmadardani/tsubaki.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '$FLUTTER_HOME/bin/flutter pub get'
            }
        }

        stage('Run Tests') {
            steps {
                sh '$FLUTTER_HOME/bin/flutter test'
            }
        }

        stage('Build APK') {
            steps {
                sh '$FLUTTER_HOME/bin/flutter build apk --release'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/build/app/outputs/flutter-apk/app-release.apk', allowEmptyArchive: true
        }
    }
}
