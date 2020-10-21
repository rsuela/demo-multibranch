pipeline {
  agent any
    stages {
      stage('Tower') {
            steps{
                wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
                    ansibleTower(
                        towerServer: 'awx',
                        jobTemplate: 'Demo Job Template',
                        importTowerLogs: true,
                        inventory: 'Demo Inventory',
                        jobTags: '',
                        limit: '',
                        removeColor: false,
                        verbose: true,
                        credential: '',
                        extraVars: '''---
                        my_var: "Jenkins Test"'''
                    )
                }
            }
        }
        stage('TPIV') {
            when {
                branch 'master'
            }
            failFast true
            parallel {
                stage('Childsupport') {
                    steps {
                        echo "Childsupport"
                    }
                }
                stage('Kiwisaver') {
                    steps {
                        echo "Kiwisaver"
                    }
                }
                stage('Studentloan') {
                    steps {
                        echo "Studentloan"
                    }
                }
            }
        }
        
        stage('Report'){
          steps {
            echo "changes v2"
          }
        }
    }
}