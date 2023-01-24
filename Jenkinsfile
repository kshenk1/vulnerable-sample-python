// Uses Declarative syntax to run commands inside a container.
pipeline {
    agent {
        kubernetes {
            yamlFile 'python-pod.yaml'
            label 'pybuild'
            defaultContainer 'pybuild'
        }
    }
    stages {
        stage('Setup') {
            steps {
                sh """
                pip install --upgrade pip
                pip install -r requirements.txt
                """
            }
        }
        stage('Linting') { // Run pylint against your code
            steps {
                script {
                    sh """
                    # pylint **/*.py
                    pylint good/*.py
                    """
                }
            }
        }
    }
}