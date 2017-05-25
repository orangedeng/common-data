pipeline {
  agent any
  stages {
    stage('clone target repo') {
      steps {
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
    stage('git pull') {
      steps {
        git(url: 'https://github.com/orangedeng/ui', branch: 'master')
      }
    }
    stage('build') {
      steps {
        sh 'docker run -v $PWD:$PWD node:6.3 ls -l $PWD'
        sh 'docker run -v $PWD:$PWD node:6.3 cat $PWD/test.txt'
      }
    }
    stage('complate') {
      steps {
        echo 'complate'
        sh '''ls -al
pwd
date'''
      }
    }
  }
}