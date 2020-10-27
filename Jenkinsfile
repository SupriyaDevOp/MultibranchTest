//def branch_name = "${BRANCH_NAME}"
pipeline {
    agent any
        
    stages {
        stage('Build') {
            steps {
                echo 'Hello from Build, This is common stage for all branches.'
				echo ${BRANCH_NAME}
            }
        }
        stage('Test') {
            steps {
                echo 'Hello from Test,  This is common stage for all branches.'
				echo ${BRANCH_NAME}
				echo 'Test'
            }
        }
       stage('feature') {
			when { 
					//branch 'feature' 
					expression {
						BRANCH_NAME ==~ ^(?:.*feature\/\w+).*$
					}
			}
            steps {
                echo 'This is common stage for all branches except feature branch.'
            }
        }
      stage('Deliver for Release') {
			when { 
				  
					//branch 'feature' 
					expression {
						BRANCH_NAME ==~ /release\/w+$/
					
				}
			}
            steps {
                echo 'This is  stage for release '
            }
	}
        stage('Deploy for Master') {
            when {
                branch 'master'
            }
            steps {
                echo 'Hello from Release,  This is only for release branch.'
            }
        }
    }
}
