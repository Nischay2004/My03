pipeline {
  agent any
  tools {
    maven 'Maven'
  }
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/Nischay2004/My03.git'
    }
  }
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts artifacts: 'target/*.war', fingerprint:true
      }
    }
    stage('Run Application') {
      steps {
        sh 'mvn clean package'
        sh 'ansible-playbook ansible/deploy.yml -i ansible/hosts.ini'
      }
    }
  }
}
