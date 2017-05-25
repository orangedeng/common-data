pipeline {
  agent any
  stages {
    stage('clone target repo') {
      steps {
        sh 'mkdir target_repo'
        git(url: 'https://github.com/orangedeng/ui', branch: 'master')
      }
    }
    stage('build') {
      steps {
        parallel(
          "build": {
            sh 'docker run -v $PWD:$PWD node:6.3 echo "123" > $PWD/test.txt'
            sh 'docker run -v $PWD:$PWD node:6.3 cat $PWD/test.txt'
            
          },
          "print workspace": {
            sh '''ls -al
pwd'''
            
          }
        )
      }
    }
    stage('approval') {
      steps {
        input(message: 'you are going to approve this', id: 'hehe made', ok: 'ok')
      }
    }
    stage('complate') {
      steps {
        echo 'run complate'
      }
    }
  }
}