pipeline {
    agent none
    tools {
        gradle "gradle"
    }
    stages {
        stage('init') {
               steps {
                script{
                  def dockerPath = tool 'docker'
                  env.PATH = "${dockerPath}/bin:${env.PATH}"
                }
               }
        }
        stage('Build') {
            agent {
                docker {
                    image 'python:2-alpine'
                }
            }
            steps {
                sh 'python -m py_compile sources/add2vals.py sources/calc.py'
            }
        }
    }
}