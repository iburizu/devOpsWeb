pipeline {
    agent any
    
    tools {
        maven 'localmaven'
    }
    environment {
        fname = "Ranjit"
        lname = "Swain"
        version = "1.2"
        system = "Dev"
    }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        
                        echo "This is made by ${env.fname} ${env.lname}"
                        echo "it's running on ${env.system} and the version is ${env.version}"
			deploy adapters: [tomcat7(credentialsId: 'StaggingTomcatserver', path: '', url: 'http://3.109.155.109:8282/')], contextPath: null, war: '**/*.war'
                    }
                }

                stage ("Deploy to Staging2"){
                    steps {
                        echo 'This is just a demo on Production server.'
                        /*script{
                            props = readProperties file: 'build.cnf'
                        }
                        echo "Current Version ${props['deploy.version']}"*/
                    }
                }
            }
        }
    }
}
