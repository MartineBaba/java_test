pipeline {
  agent any
  stages {
    stage('test') {
      environment {
        var1 = 'bonjour'
      }
      steps {
        deleteDir()
        echo 'hello phase de test'
        sh 'mvn clean test'
        sh 'touch bonjour'
      }
    }

    stage('reports') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('end') {
      steps {
        sh 'echo " Fin des taches, ca c\'est bien passé"'
      }
    }

  }
}