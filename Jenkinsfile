pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Compile the .cpp file using a shell script
                    sh "g++ -o output_file helloworld.cpp"
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Print the output of the .cpp file using a shell script
                    sh "./output_file"
                }
            }
        }
        stage('Deploy') {
            steps {
                // Deploy the application (add deployment steps here)
                // For example, deploy to a server, container, etc.
            }
        }
    }
    
    post {
        always {
            // Display "pipeline failed" in case of any errors within the pipeline
            catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
                echo "Pipeline passed successfully!"
            }
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                echo "Pipeline failed!"
            }
        }
    }
}
