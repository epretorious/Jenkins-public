pipeline {
    // From the Jenkins-public repository on Github...
    agent any
    parameters {
        choice(name: 'DIRECTION', choices: ['Coming', 'Going'], description: 'Are you coming or going?')
        string(name: 'NAME', description: 'Your name?', defaultValue: 'World')
    }
    stages {
        stage('Hello') {
            when {
                expression { params.DIRECTION == 'Coming' }
            }
            steps {
                echo "Hello, ${params.NAME}!"
            }
        }
        stage('CruelWorld') {
            when {
                allOf {
                    expression { params.DIRECTION == 'Going' }
                    expression { params.NAME == 'World' }
                }
            }
            steps {
                echo "Goodbye, cruel ${params.NAME}!"
            }
        }
        stage('Goodbye') {
            when {
                expression { params.DIRECTION == 'Going' }
            }
            steps {
                echo "Goodbye, ${params.NAME}!"
            }
        }
    }
}
