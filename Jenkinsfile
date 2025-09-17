pipeline {
    agent any

    environment {
        TESTVALUE = 'value1''' // Corrected assignment with quotes
    }

    options {
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
        timeout(time: 12, unit: 'HOURS')
        timestamps()
    }

    triggers {
        cron('@midnight')
    }

    stages {
        stage('Requirements') {
            steps {
                echo 'Starting Requirements stage...'
                script {
                    if (env.TESTVALUE == 'value1') {
                        echo "Value = ${env.TESTVALUE} is valid."
                    }
                }
                echo 'Installing requirements...'
            }
        }
        stage('Build') {
            steps {
                echo 'Starting Build stage...'
                script {
                    if (env.TESTVALUE == 'value2') {
                        echo "Value = ${env.TESTVALUE} is valid."
                    }
                }
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Starting Test stage...'
                script {
                    if (env.TESTVALUE == 'value3') {
                        echo "Value = ${env.TESTVALUE} is valid."
                    }
                }
                echo 'Testing..'
            }
        }
        stage('Report') {
            steps {
                echo 'Starting Report stage...'
                echo 'Reporting....'
            }
        }
    }

    post {
        always {
            echo "This step will run after all other steps have finished. It will always run, even if the status of the build is not SUCCESS"
        }
    }
}
