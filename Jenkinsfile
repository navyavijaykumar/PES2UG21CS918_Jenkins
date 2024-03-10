pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Compile the .cpp file using shell script
                sh 'g++ -o a hello.cpp'
            }
        }
        stage('Test') {
            steps {
                // Print output of .cpp file using shell script
                sh './a'
            }
        }
        stage('Deploy') {
            steps {
                // Add deployment steps here (if any)
                echo 'Deployment steps...'
            }
        }
    }
    
    post {
        always {
            // Display "pipeline failed" in case of any errors within the pipeline
            catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
                echo "Pipeline failed!"
            }
        }
    }
}
