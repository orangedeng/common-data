pipeline {
  agent any
  stages {
    stage('clone target repo') {
      steps {
        git(url: 'https://github.com/orangedeng/ui', branch: 'master')
        sh '''ls -al
pwd
date'''
      }
    }
    stage('approval one') {
      steps {
        input(message: 'approval one', id: 'a1', ok: 'ok')
      }
    }
    stage('build') {
      steps {
        sh 'docker run -v $PWD:$PWD node:6.3 echo "123" > $PWD/test.txt'
        sh 'docker run -v $PWD:$PWD node:6.3 cat $PWD/test.txt'
        sh '''ls -al
pwd
date'''
      }
    }
    stage('complate') {
      steps {
        echo 'complate'
      }
    }
  }
}