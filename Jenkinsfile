pipeline {
    agent {
        node{
            label 'Agent-1'
        }
    }
    environment{
        COURSE = "Jenkins"
    }
    options{
        timeout(time: 10, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        booleanParam(name: 'DEBUG_MODE', defaultValue: true, description: 'Enable debug output?')
        choice(name: 'ENVIRONMENT', choices: ['dev', 'staging', 'prod'], description: 'Target environment')
    }
    stages {
        stage('Build') {
            steps {
                script{
                    sh """
                        echo "Building"
                        # sleep 10
                        echo $COURSE
                        env
                    """
                }
            }
        }
        stage('Test') {
            steps {
                script{
                    sh """
                        echo "Testing"
                    """
                }
            }
        }
        stage('Deploy') {
            steps {
                script{
                    sh """
                        echo "Deploying"
                    """
                }
            }
        }
    }
    post{
        always{
            echo "I will always say Hello again!"
            cleanWs()
        }
        success{
            echo "I will run if success"
        }
        failure{
            echo "I will run if failure"
        }
        aborted{
            echo "Pipeline is aborted"
        }
    }
}