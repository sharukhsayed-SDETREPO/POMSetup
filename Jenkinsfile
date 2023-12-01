pipeline {
  agent any
  stages {
    stage('Build QA') {
      parallel {
        stage('Build QA') {
          steps {
            echo 'Run on QA'
          }
        }

        stage('chrome') {
          steps {
            echo 'Building on chrome'
          }
        }

        stage('edge') {
          steps {
            echo 'build on edge'
          }
        }

      }
    }

    stage('Run on QA') {
      parallel {
        stage('Run on QA') {
          steps {
            sh 'echo \'Run on QA\''
          }
        }

        stage('Run on chrome') {
          steps {
            echo 'Run on chrome'
          }
        }

        stage('run on edge') {
          steps {
            echo 'Run on edge'
          }
        }

      }
    }

    stage('Run on stage') {
      steps {
        echo 'stage execution'
      }
    }

    stage('Run on PROD') {
      steps {
        echo 'Run on PROD'
      }
    }

  }
}