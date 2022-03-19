pipeline {
	agent any
	stages {
		stage('Stage 1') {
			steps {
				echo 'Hello World!'
			}
		}

		stage('Push Notification') {
			steps {
				script {
					withCredentials([string(credentialsId: ‘telegramToken’, variable: ‘TOKEN’), string(credentialsId: ‘telegramChatId’, variable: ‘CHAT_ID’)]) {
						sh ("""
						curl -s -X POST https://api.telegram.org/bot${TOKEN}/sendMessage -d chat_id=${CHAT_ID} -d parse_mode="HTML" -d text="<b>Project</b>:Pipeline \ <b>Branch</b>:main \ <b>Build</b>:OK \ <b>Test suite</b>=Passed"
						""")
					}
				}
			}
		}
	}
}
