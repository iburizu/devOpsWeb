
pipeline{
    agent {
        label "java"
    }
    stages{
        stage ('Build'){
            steps {
                echo "Building"
                echo "............."
                echo "Build completed"
                }
        }
        stage ('Test') {
            steps{
                echo "Testing"
                echo "............"
                echo "Testing Completed"
            }
        }
        stage ('Deploy') {
            steps{
                echo "Deploying"
                echo ".............."
                echo "Deploy is completed"
            }
        }
    }
}
