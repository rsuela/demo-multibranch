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
                    agent {
                        label "windows"
                    }
                    steps {
                        echo "Childsupport"
                    }
                }
                stage('Kiwisaver') {
                    agent {
                        label "windows"
                    }
                    steps {
                        echo "Kiwisaver"
                    }
                }
                stage('Studentloan') {
                    agent {
                        label "windows"
                    }
                    steps {
                        echo "Studentloan"
                    }
                }
            }
        }
    }
}