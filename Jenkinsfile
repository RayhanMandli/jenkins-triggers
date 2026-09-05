def COLOR_MAP = [
    'SUCCESS' : 'good',
    'FAILURE' : 'danger',
]

pipeline{

agent any

stages{

stage("Build"){

steps{

	sh 'echo "Build complete"'

}

}

}

post {
        always {
            echo 'Slack Notification: Build completed.'
            slackSend channel: '#jenkins-notifications',
            color: COLOR_MAP[currentBuild.currentResult],
            message: "Build ${currentBuild.currentResult}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"
        }
    }

}
