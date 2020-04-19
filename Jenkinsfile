def gv
pipeline{
    agent any
    options { skipDefaultCheckout() }
    environment{
        VERSION = '1.0.0'
        CRED = credentials('gituser')
    }
	parameters{
		choice(name: 'VERSION1', choices: ['1.0.0','2.0.0','3.0.0'], description: 'version control')
		booleanParam(name: 'TEST', defaultValue: true, description: 'for testing')
	}
    stages{
        stage("Checkout"){
            steps{
            checkout scm
            }
        }
        stage("Build"){
            steps{
                        withCredentials{
                        [usernamePassword(Credentials: 'gituser',usernameVariable: USER , passwordVariable: PWD)]
                    }
                    {echo "${USER} ${PWD}"}
				script{
					gv = load "script.groovy"
					gv.buildapp()
				}
            }
        }
        stage("Deploy") {
		when {
			expression{
				params.TEST
			}
		}
            steps{
                echo "crdentials ${CRED}"
                script{
					gv.deployapp()
				}
            }
        }
    }
}
