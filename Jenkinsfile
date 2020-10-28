pipeline {
    agent any
        
    stages {
        stage('Build') {
            steps {
                echo 'Hello from Build, This is common stage for all branches.'
				echo "${env.BRANCH_NAME}"
            }
        }
        stage('Test') {
            steps {
                echo 'Hello from Test,  This is common stage for all branches.'
				echo "${env.BRANCH_NAME}"
            }
        }
        stage('Feature') {
			when {
					expression {
						isFeature = (env.BRANCH_NAME ==~ /^(?:.*feature\/\w+).*$/)
						echo "isFeature: ${isFeature}"
						return isFeature
					}
			}
            steps {
                echo 'This is stage for feature branch.'
            }
        }
		stage('Release') {
			when {
					expression {
						isRelease = (env.BRANCH_NAME ==~ /^(?:.*release\/\w+).*$/)
						echo "isRelease: ${isRelease}"
						return isRelease
					}
			}
            steps {
                echo 'This is stage for release branch.'
            }
		}
        stage('Master') {
            when {
					expression {
						isMaster = (env.BRANCH_NAME ==~ /^(?:.*master\/\w+).*$/)
						echo "isMaster: ${isMaster}"
						return isMaster
					}
			}
            steps {
                echo 'This is stage for Master branch.'
            }
        }
    }
}