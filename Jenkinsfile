pipeline {
  agent any
  stages {
    stage('test') {
      parallel {
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

        stage('build') {
          environment {
            JAVA_HOME = '/usr/lib/jvm/java-8-openjdk/'
          }
          steps {
            sh 'git clone https://github.com/kliakos/sparkjava-war-example.git'
            sh 'ls'
            sh 'cd sparkjava-war-exemple'
            sh 'mvn clean install'
            archiveArtifacts 'target/*.war'
          }
        }

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