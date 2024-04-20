pipeline {
  agent any
  stages {
    stage('Build DEV') {
      parallel {
        stage('Build deV') {
          steps {
            sh 'mvn clean install -DskipTests=true'
          }
        }

        stage('run test on dev') {
          steps {
            sh 'mvn test -Denv=dev'
          }
        }

      }
    }



    stage('Publish Allure Reports for Sanity') {
           steps {
                script {
                    allure([
                        includeProperties: false,
                        jdk: '',
                        properties: [],
                        reportBuildPolicy: 'ALWAYS',
                        results: [[path: '/allure-results']]
                    ])
                }
            }
        }
        
        
        	stage('Publish  Extent Report for Sanity'){
            steps{
                     publishHTML([allowMissing: false,
                                  alwaysLinkToLastBuild: false, 
                                  keepAll: false, 
                                  reportDir: 'reports', 
                                  reportFiles: 'APIExecutionReport.html', 
                                  reportName: 'API HTML Regression Extent Report Sanity', 
                                  reportTitles: ''])
            }
        } 
    stage('Build QA') {
      parallel {
        stage('Build QA') {
          steps {
            sh 'mvn compile'
          }
        }

        stage('run test on qa') {
          steps {
            sh 'mvn test -Denv=qa'
          }
        }

      }
    }

    stage('Build stage') {
      parallel {
        stage('Build stage') {
          steps {
            sh 'mvn compile'
          }
        }

        stage('no env run') {
          steps {
            sh 'mvn test'
          }
        }

      }
    }

  }
}