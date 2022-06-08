pipeline {
  agent any
  stages {
    stage('test') {
      environment {
        var1 = 'bonjour'
      }
      steps {
        echo 'hello phase de test'
        sh 'mvn clean test'
        sh 'touch bonjour'
        junit 'target/surefire-reports/*.xml'
        cleanWs(cleanWhenSuccess: true)
      }
    }

    stage('build') {
      steps {
        git(url: 'https://github.com/kliakos/sparkjava-war-example.git', branch: 'master')
        sh 'mvn clean install'
      }
    }

    stage('end') {
      steps {
        sh 'echo " Fin des taches, ca c\'est bien passé"'
      }
    }

  }
}