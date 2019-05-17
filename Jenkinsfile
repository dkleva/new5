pipeline {

   environment {
     registry = "dkgnim/new1"
     registryCredential = '044ff476-3603-4b5f-9157-abe9a11ebd7d'
     dockerImage = ''
   }
   agent any

   stages {
        stage ('Initialize1') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }


        stage ('build') {
            steps {
               sh 'hostname'
               sh 'mvn package'
               sh 'mvn clean deploy'

        }
      }

        stage ('docker build image') {
            steps{
               script {
                   dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
        }

        stage('Deploy Image') {
            steps{
                script {
                   docker.withRegistry( '', registryCredential ) {
                   dockerImage.push()
          }
        }
      }
    }
}
}
