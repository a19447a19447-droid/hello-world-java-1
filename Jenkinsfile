pipeline {
    agent any
    environment {
        JAVA_HOME = 'C:\\Program Files\\Java\\jdk-21.0.10' // Set the path to your JDK
        PATH = "${env.JAVA_HOME}\\bin;${env.PATH}" // Add JDK bin to PATH
    }



    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/a19447a19447-droid/hello-world-java-1.git'
            }
        }
        stage('Build') {
            steps { bat 'gradlew clean build'}
        }
        stage('Test') {
            steps { bat 'gradlew test'}
        }
        stage('Deploy') {
            steps { bat 'java -jar build/libs/hello-world-java-V1.0.jar'}           
        }    
}

post {
        always {
            echo 'Cleaning up workspace'
            deleteDir() // Clean up the workspace after the build
        }
        success {
            echo 'Build succeeded!!!'
            // You could add notification steps here
        }
        failure {
            echo 'Build failed!'
            // You could add notification steps here
        }
    }
    
}
