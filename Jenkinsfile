#!/usr/bin/env groovy

// 単体テスト実行ブランチ(develop/～のみ実施)
def TARGET_BRANCH = 'develop'

pipeline {

    //実行コンテナ」を設定
    agent{
        label 'maven:3.6.3-jdk-8'
    }

    stages{

        //チェックアウト
        stage('Checkout'){
            steps{
                script{
                    //チェックアウト
                    checkout scm
                }
            }
        }

        //ビルド
        stage('Build'){
            steps{
                script{
                    sh "mvn package"
                }
            }
        }
    }

    post{
        always{
            //成果物保存
            archiveArtifacts artifacts: '**/*jar', fingerprint: true
        }
        failure{
            echo "エラー"
            //mail bcc: 'BCCメールアドレスを記載する', body: '通知内容を記載する', cc: 'CCメールアドレスを記載する', from: '', replyTo: '', subject: '件名を記載する', to: '宛先メールアドレスを記載する'
        }
        success{
            echo "正常"
            //mail bcc: 'BCCメールアドレスを記載する', body: '通知内容を記載する', cc: 'CCメールアドレスを記載する', from: '', replyTo: '', subject: '件名を記載する', to: '宛先メールアドレスを記載する'
        }
        unstable{
            echo "不安定"
            //mail bcc: 'BCCメールアドレスを記載する', body: '通知内容を記載する', cc: 'CCメールアドレスを記載する', from: '', replyTo: '', subject: '件名を記載する', to: '宛先メールアドレスを記載する'
        }
    }
}
