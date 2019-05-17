pipeline {
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

}
}
