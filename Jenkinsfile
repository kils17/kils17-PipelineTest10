pipeline {
    agent none
        stages {
            stage('Deploy') {
                steps {
                    echo 'Application Deploy'
                }
            }
            stage('Parallel Env Tests') {
                parallel {
                    stage('Test on Docker Image') {
                        agent any
                        steps {
                            echo 'Here is Docker'
                        }
                    }
                    stage('Test on Windows 10') {
                        agent any
                        steps {
                            echo 'Here is Windows'
                        }
                    }
                }
            }
        }
    post {
        success {
            // 빌드의 결과가 성공일경우 
            //resultSlackSend("good", "SUCCESS")
            slackSend color: '#00FF00', message: 'PipelineTest10 - Success'
        }
        failure {
            // 빌드의 결과가 실패일경우 
            //resultSlackSend("danger", "FAILURE")
            slackSend color: '#FF0000', message: 'PipelineTest10 - FAILURE'
        }
        aborted {
            // 빌드를 중간에 멈추는 경우
            //resultSlackSend("warning", "ABORTED")
            slackSend color: '#FFFF00', message: 'PipelineTest10 - ABORTED'
        }
    }
}
